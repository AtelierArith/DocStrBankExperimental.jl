```
UA_USERACCESSLEVEL(; read = false, write = false, historyread = false, 
        historywrite = false, semanticchange = false, statuswrite = false, 
        timestampwrite = false)::UInt8
```

calculates a `UInt8` number expressing how the value of a variable can be accessed. Default is to disallow all operations. The meaning of the keywords is explained here: [OPC Foundation website](https://reference.opcfoundation.org/Core/Part3/v105/docs/8.57)
