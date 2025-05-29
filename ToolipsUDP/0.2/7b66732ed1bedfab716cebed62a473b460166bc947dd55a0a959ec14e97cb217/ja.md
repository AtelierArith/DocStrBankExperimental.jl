```julia
send(c::UDPConnection, data::String, to::IP4 = "127.0.0.1":2000) -> ::Nothing
```

`UDPConnection`から任意のエンドポイントに`data`を送信します。これは、`UDPHandler`内で送信したいデータに便利です。現在のクライアントに応答するために、`to`として`c.ip`を提供することもできますが、`respond!`を使用してプロセスを簡素化することもできます。これは、ベーススレッドからのみ行うことができることに注意してください。将来的には、このデータを変換する方法があるかもしれませんが、現在はサポートされていません。マルチスレッドのデータに対する追加は、頭痛の種であるだけでなく、それを使用しない他の人にとってもストレスになることを理解してください – 複数のスレッドでそれを複製しているためです。

```julia
module UserTracker
using ToolipsUDP

users = Dict{IP4, String}()

main_handler = handler() do c::UDPConnection
    if contains(c.packet, " ") || c.packet == ""
        respond!(c, "please provide a name to name yourself")
        return
    end
    push!(users, get_ip4(c) => c.packet)
    # みんなに参加メッセージが送信されます。
    [send(c, "$(c.packet) joined", user_ip) for user_ip in keys(users)]
end

export main_handler, UDP, start!
end
```
