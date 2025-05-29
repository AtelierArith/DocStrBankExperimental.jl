```julia
respond!(c::AbstractConnection, args ...) -> ::Nothing
```

A more articulated response from a `Toolips` server, `respond!` allows us to add custom  headers to our HTTP response, respond with different codes, and set cookies.

```julia
# base method (mostly internal)
respond!(c::AbstractConnection, resp::HTTP.Response, headers::Pair{String, String} ...)
# regular headers/code dispatch
respond!(c::AbstractConnection, body::String = "", headers::Pair{String, String} ...; code::Int64 = 200)
```

The `Vector{Cookie}` dispatch, for setting cookies on response (see `Cookie` and `get_cookies`):

```julia
respond!(c::AbstractConnection, body::String, cookies::Vector{Cookie}, headers::Pair{String, String} ...; 
    code::Int64 = 20)
```

description of method list

  * See also: `write!`, `get_target`, `Connection`, `route`, `start!`
