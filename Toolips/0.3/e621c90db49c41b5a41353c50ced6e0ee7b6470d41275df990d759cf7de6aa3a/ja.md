  * 標準のWebサーバーを起動する:

```julia
start!(mod::Module = Main, ip::IP4 = ip4_cli(Main.ARGS);
    threads::Int64 = 1, router_threads::UnitRange{Int64} = -2:threads, router_type::Type{<:AbstractRoute} = AbstractRoute, 
    async::Bool = true)
```

  * 拡張サーバーの場合:

```julia
start!(st::Type{ServerTemplate{<:Any}}, mod::Module = Toolips.server_cli(Main.ARGS); keyargs ...)
```

`start!`は新しいサーバーを起動するために`Toolips`サーバー`Module`で使用されます。`threads`を指定すると、付随する`ProcessManager`のために生成されるスレッドの総数が設定されます。`router_threads`はルーターがスレッドをどのように処理するかを決定します。この範囲内のすべてのスレッドは`0`までがベーススレッドとなるため、例えば`-2:threads`はベーススレッドの`-2`、`-1`、`0`で3つのクライアントにサービスを提供し、その後最初のスレッド`1`に移動し、次に`2`に進むという具合です。

```julia
module MyExampleServer
using Toolips

home = route("/") do c::AbstractConnection
   write!(c, "hello world!")
end

export home, start!
end

using Main.MyExampleServer; start!(Main.MyExampleServer)
```

  * 参照: `route!`, `AbstractExtension`, `route`, `kill!`, `start!`
