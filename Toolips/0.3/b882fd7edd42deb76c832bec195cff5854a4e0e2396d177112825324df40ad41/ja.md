  * 標準のWebサーバーを開始する:

```julia
start!(mod::Module = Main, ip::IP4 = ip4_cli(Main.ARGS);
    threads::Int64 = 1, router_threads::UnitRange{Int64} = -2:threads, router_type::Type{<:AbstractRoute} = AbstractRoute, 
    async::Bool = true)
```

  * 拡張サーバーの場合:

```julia
start!(st::Type{ServerTemplate{<:Any}}, mod::Module = Toolips.server_cli(Main.ARGS); keyargs ...)
start!(st::Symbol, mod::Module, args ...; keyargs ...)
```

  * (拡張) `TCP`サーバー用（HTTPなし）:

```julia
start!(st::ServerTemplate{:TCP}, mod::Module = Main, ip::IP4 = ip4_cli(Main.ARGS), 
    threads::Int64 = 1, async::Bool = false)
```

`start!`は新しいサーバーを開始するために`Toolips`サーバー`Module`で使用されます。`threads`を提供することで、付随する`ProcessManager`のために生成するスレッドの総数を設定します。`router_threads`はルーターがスレッドをどのように処理するかを決定します。この範囲内のすべてのスレッドは`0`までが基本スレッドとなるため、`-2:threads` – 例えば – は基本スレッドで3つのクライアントを処理し、-2、-1、0の後、最初のスレッド1に移動し、次に2に移動し、というようになります。

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
