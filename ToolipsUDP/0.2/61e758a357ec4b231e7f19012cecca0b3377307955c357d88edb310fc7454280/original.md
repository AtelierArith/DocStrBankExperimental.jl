Created in June, 2022 by [chifi - an open source software dynasty.](https://github.com/orgs/ChifiSource) by team

### ToolipsUDP

`ToolipsUDP` brings `Toolips` web-development conventions to the format of UDP. This package allows for  the creation of extensible and versatile UDP servers for Julia.

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

The API provides the obvious `get_ip` binding, as well as `send` and `respond!` for convenient  peer-to-server communication.

##### provides

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
