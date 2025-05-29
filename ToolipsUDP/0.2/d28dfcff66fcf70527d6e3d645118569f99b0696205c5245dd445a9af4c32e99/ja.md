```julia
start!(st::Type{ServerTemplate{:UDP}}, mod::Module; ip::IP4 = "127.0.0.1":2000, threads::UnitRange{Int64} = 1:1, 
    async::Bool = true)
```

`ToolipsUDPServer`としてサーバーモジュールを開始します。`UDP`は`ToolipsUDP`からの定数として提供され、サーバーを`UDPServer`として開始するために提供されます。この引数なしで`start!`を呼び出すと、`Toolips`ウェブサーバーを開始しようとしていることになります - これにより、`default_404`ルートのみを持つサーバーが結果として得られます。`threads`は`handler`(s)を提供するスレッドの数を決定します。

```julia
module MyServer
using ToolipsUDP

responder = handler() do c::UDPConnection
    data = c.packet
    println(c.packet)
end

export responder
end

using ToolipsUDP; start!(UDP, MyServer)
```

**注意**：マルチスレッドを使用する場合、ハンドラーの`Connection`を`AbstractUDPConnection`として注釈を付けることをお勧めします。これにより、実際にスレッド間で送信できる`IOConnection`が促進されます。
