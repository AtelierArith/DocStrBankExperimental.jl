```julia
handler(f::Function, ...) -> ::AbstractUDPHandler
```

The `handler` `Function` creates a `UDPHandler` that handles  incoming packets and responds to them. If a `Function` is provided,  we will get a `UDPHandler`. If a `Function` and a `String` are provided, we  get a `NamedHandler` in return.

```julia
handler(f::Function) -> ::UDPHandler
handler(f::Function, name::String) -> ::NamedHandler
```

---

```example
module SampleServer

sample_handler = handler() do c::UDPConnection
                           # ^ ::AbstractUDPConnection when multi-threading.
    println("handled a client")
end

export sample_handler
end
```
