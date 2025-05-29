  * start a standard WebServer:

```julia
start!(mod::Module = Main, ip::IP4 = ip4_cli(Main.ARGS);
    threads::Int64 = 1, router_threads::UnitRange{Int64} = -2:threads, router_type::Type{<:AbstractRoute} = AbstractRoute, 
    async::Bool = true)
```

  * for extended servers:

```julia
start!(st::Type{ServerTemplate{<:Any}}, mod::Module = Toolips.server_cli(Main.ARGS); keyargs ...)
start!(st::Symbol, mod::Module, args ...; keyargs ...)
```

  * (extension) for a `TCP` server (no HTTP):

```julia
start!(st::ServerTemplate{:TCP}, mod::Module = Main, ip::IP4 = ip4_cli(Main.ARGS), 
    threads::Int64 = 1, async::Bool = false)
```

`start!` is used on a `Toolips` server `Module` to start a new server. Providing `threads` sets  the total amount of threads to spawn for the accompanying `ProcessManager`. `router_threads` will      determine how the router handles threads.  Every thread in this range until `0` will be the base      thread, so `-2:threads` – for example – will serve 3 clients with the base threads, -2, -1, 0,       and then move onto the first thread with 1, moving onto 2, and so-forth.

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

  * See also: `route!`, `AbstractExtension`, `route`, `kill!`, `start!`
