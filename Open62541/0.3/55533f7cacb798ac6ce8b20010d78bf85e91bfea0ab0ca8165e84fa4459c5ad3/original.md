```
value = JUA_Client_readValueAttribute(client::JUA_Client, nodeId::JUA_NodeId, type = Any)
```

uses the client API to read the value of `nodeId` from the server that the `client` is connected to.

The output `value` is automatically converted to a Julia type (such as Float64, String, Vector{String}, etc.) if possible. Otherwise, open62541 composite types are returned.

Note: Since it is unknown what type of value is stored within `nodeId` before reading it, this function is inherently type unstable.

Type stability is improved if the optional argument `type` is provided, for example, if you know that you have stored a Matrix{Float64} in `nodeId`, then you should specify this. If the wrong type is specified, the function will throw a TypeError.
