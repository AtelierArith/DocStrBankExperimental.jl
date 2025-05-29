2022年6月に[chifi - an open source software dynasty.](https://github.com/orgs/ChifiSource)によってチームによって作成されました

### ToolipsUDP

`ToolipsUDP`は、`Toolips`のウェブ開発の慣習をUDPの形式に持ち込みます。このパッケージは、Julia用の拡張可能で多用途なUDPサーバーの作成を可能にします。

```julia
module NewServer
using ToolipsUDP

new_handler = handler() do c::UDPConnection
    respond!(c, "hello")
end

export new_handler, start!, UDP
end

using NewServer; start!(UDP, NewServer)
```

APIは明示的な`get_ip`バインディングに加え、便利なピアからサーバーへの通信のための`send`と`respond!`を提供します。

##### 提供するもの

  * `UDP` (`ServerTemplate{:UDP}`)
  * `AbstractUDPHandler`
  * `UDPHandler`
  * `NamedHandler`
  * `handler`
  * `AbstractUDPConnection`
  * `UDPConnection`
  * `UDPIOConnection`
  * `AbstractUDPExtension`
  * `UDPExtension{T <: Any}`
  * `Toolips.route!(c::UDPConnection, ext::AbstractUDPExtension)`
  * `Toolips.on_start(data::Dict{Symbol, Any}, ext::AbstractUDPExtension)`
  * `Toolips.start!(st::Type{ServerTemplate{:UDP}}, mod::Module; ip::IP4 = "127.0.0.1":2000, threads::UnitRange{Int64} = 1:1, async::Bool = true)`
  * `Toolips.new_app(st::Type{ServerTemplate{:UDP}}, name::String)`
  * `Toolips.get_ip(c::UDPConnection)`
  * `get_ip4`
  * `send`
  * `respond!`
  * `MultiHandler`
  * `set_handler!`
  * `remove_handler!`
  * `Toolips.route!(c::UDPConnection, mh::MultiHandler)`
