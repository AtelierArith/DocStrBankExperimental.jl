```julia
set_handler!(c::UDPConnection, args ...) -> ::Nothing
```

`c`によって現在処理されているクライアントのための`MultiHandler`に`NamedHandler`を設定します。

```julia
# 現在のクライアントのため
set_handler!(c::UDPConnection, name::String)
# 他のクライアントのため
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
    respond!(c, "you made it to the second screen!")
end

multi_handler = ToolipsUDP.MultiHandler(main_handler)

export multi_handler, start!, UDP
export main_handler, second_step
end
```
