```
UA_USERWRITEMASK(; accesslevel = false, arraydimensions = false,
        browsename = false, containsnoloops = false, datatype = false,
        description = false, displayname = false, eventnotifier = false,
        executable = false, historizing = false, inversename = false,
        isabstract = false, minimumsamplinginterval = false, nodeclass = false,
        nodeid = false, symmetric = false, useraccesslevel = false, 
        userexecutable = false, userwritemask = false, valuerank = false,
        writemask = false, valueforvariabletype = false)::UInt32
```

calculates a `UInt32` number expressing which attributes of a node are writeable. The meaning of the keywords is explained here: [OPC Foundation website](https://reference.opcfoundation.org/Core/Part3/v105/docs/8.60)

If the specific node type does not support an attribute, the corresponding keyword must be set to false. *This is currently not enforced automatically.*
