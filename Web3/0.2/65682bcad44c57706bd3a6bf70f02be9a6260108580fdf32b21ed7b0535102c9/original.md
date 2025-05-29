```
encodefunctioncall(f::ABIFunction, inputs::Array) -> data
encodefunctioncall(io::IO, f::ABIFunction, inputs::Array)
encodefunctioncall(io::IOBuffer, f::ABIFunction, inputs::Array) -> data
```

Encode a call to a function
