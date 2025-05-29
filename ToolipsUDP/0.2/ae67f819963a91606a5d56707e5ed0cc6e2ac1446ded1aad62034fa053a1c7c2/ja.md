```julia
remove_handler!(c::UDPConnection) -> ::Nothing
```

現在選択されている `NamedHandler` を削除し、クライアントを `MultiHandler` に提供された `main_handler` に戻します。

```julia
# 現在のクライアント用
set_handler!(c::UDPConnection, name::String)
# 他のクライアント用
set_handler!(c::UDPConnection, ip4::IP4, name::String)
```

```example
module HandlerSample
using ToolipsUDP


main_handler = handler() do c::UDPConnection
    println("response 1")
    set_handler!(c, "second")
end

second_step = handler("second") do c::UDPConnection
    println("response 2")
    remove_hanlder!(c)
end

multi_handler = ToolipsUDP.MultiHandler(main_handler)

export multi_handler, start!, UDP
export main_handler, second_step
end

# このサーバーは、response 1 と response 2 の間を継続的に切り替えます。
```
