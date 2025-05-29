```julia
handler(f::Function, ...) -> ::AbstractUDPHandler
```

`handler` `Function`は、受信パケットを処理し、それに応答する`UDPHandler`を作成します。`Function`が提供されると、`UDPHandler`が得られます。`Function`と`String`が提供されると、`NamedHandler`が返されます。

```julia
handler(f::Function) -> ::UDPHandler
handler(f::Function, name::String) -> ::NamedHandler
```

---

```example
module SampleServer

sample_handler = handler() do c::UDPConnection
                           # ^ ::AbstractUDPConnectionはマルチスレッド時。
    println("クライアントを処理しました")
end

export sample_handler
end
```
