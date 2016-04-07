# Node.js Multi-VM

This repository is for discussion of and work related to multiple VM related issues and ideas for Node.js

## Why does this repository exist?

As part of the recent "VM Summit" held on April 5 and 6th, 2016 to discuss the possibility of and issues around supporting multiple VMs in Node.js, it was decided that a separate repository that can be used to discuss the details and work on the ideas would be helpful. This is *not* a code repository, however. It exists mainly so that we can have a place for issue tracking, working through proposals, and so forth before they're ready to go to the other main code repositories. 

## What happened at this VM Summit thing anyway?

Node.js collaborators got together with members of the V8 team from Google and the Chakra team from Microsoft to discuss the issues around supporting multiple VMs. The two day meeting was hosted by IBM at the IBM Foster City location. We were able to get through quite a bit and there will be a write up shortly of the notes. Preliminary details can be found here: http://github.com/jasnell/vm-summit. Most importantly, however, @trevnorris was able to find dessert and I'm fairly certain @dshaw volunteered to do all the real work.

Expect a detailed report of the VM Summit to be written up over the next couple of days.

## What are the next steps

Coming out of the VM Summit we identified a number of very specific actions, the details of which should be filled in soon:

1. @mhdawson, @ianwjhalliday, and @stefanmb will be working on a concrete proposal that is essentially an evolved NAN that would allow greater isolation for Native Module Developers from the specific details of the VM implementation. The specific goal is to make it possible to isolate native module developers from API/ABI changes that may occur when we update or change the underlying VM implementation.

2. @ofrobots will kick off a discussion in the V8 team about exploring the possibility of implementing an efficient dynamic FFI capability within the VM itself. The specific goal would be to make it easier for JS to call into the C/C++ layer without the need for VM-specific APIs and wrappers. It is believed that doing so would make it easier for developers to be isolated from API/ABI changes that occur in the VM layer. This is a more speculative piece of work.

3. @piscisaureus is compiling the high level motivations, benefits, and costs of working on a multi-VM Node.js for review by the @nodejs/ctc. This will answer the question of, "Why are we doing this" and would lay out the fundamental structure for moving forward. This would be put onto the CTC agenda for discussion and presented either by @piscisaureus or @jasnell.

4. If we do go down the multi-VM route, there will be a significant need to be able to certify that although such-n-such build of Node.js may use a different VM implementation, it's still Node.js and still meets a minimum expectation of functionality. To this end, @joshgav and @jasnell will be exploring what "compliance" means in terms of Node.js. @joshgav will be continuing a survey of the existing surface area of Node.js' use of the V8 APIs, helping to document the various assumptions that Node.js makes of the VM and of what it provides. @jasnell will be looking at the [TC39/test262](https://github.com/tc39/test262) tests to identify what minimal subset of EcmaScript features *must* be supported by any VM that sits under Node.js in order for it still to be called Node.js.

The attendees of the VM summit will be planning to meet again on a conference call in about a month to check in on the progress of these items.

Additional details will be filled in later.
