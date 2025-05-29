```
output::Union{Any, Tuple{Any, ...}} = JUA_Client_call(client::JUA_Client, 
    parentnodeid::JUA_NodeId, methodid::JUA_NodeId, inputs::Union{Any, Tuple{Any, ...}})
```

uses the client API to call a method node (`methodid`) on the server the `client` is connected with.  `inputs` can either be a single argument or a tuple of arguments. Depending on the method called an apporpriate output or tuple of output arguments is returned.
