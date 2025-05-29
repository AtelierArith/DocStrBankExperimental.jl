```
UA_Server_call(server::Ptr{UA_Server}, request::Ptr{UA_CallMethodRequest}, result::Ptr{UA_CallMethodResult})::Nothing
```

uses the server API to process the method call request `request` on the `server`. Note that `result` is mutated.
