```julia
Connection <: AbstractConnection
```

  * `stream`**::HTTP.Stream**
  * `data`**::Dict{Symbol, Any}**
  * `routes`**::Vector{<:AbstractRoute}**

The `Connection` is the main type a `Toolips` server uses to serve an incoming  HTTP request. Indexing the `Connection` yields routes or server data when a `String` or  `Symbol` is used. A `Connection` can also be written to with `write!`. Arguments, and  other client information can be retrieved with the various *get* functions for an `AbstractConnection`.

```julia
get_args(c::AbstractConnection)
get_ip(c::AbstractConnection)
get_post(c::AbstractConnection)
get_route(c::AbstractConnection)
get_method(c::AbstractConnection)
get_parent(c::AbstractConnection)
get_client_system(c::AbstractConnection)
```

```julia
proxy_pass!(c::Connection, url::String)
```

A `Connection` is provided directly to your route's handler `Function` as its only argument.  When we create a `Route` with `route`, we will be passed a `Connection` which we can  then use with `write!` to respond.

```example
module SampleServer
using Toolips
        # annotating gives multiple dispatch to routes (recommended)
home = route("/") do c::Connection
    write!(c, "hello world!")
end

export home, start!
end
```

`Servables` are also binded to `write!`, so a `Connection` can easily serve `Components`.

  * See also: `route`, `AbstractConnection`, `route!`, `write!`, `Components`, `IOConnection`, `MobileConnection`
