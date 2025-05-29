```julia
get_args(c::AbstractConnection) -> ::Dict{Symbol, String}
```

Returns the `GET` arguments of the current `Connection` in a `Dict{Symbol, String}`.

```example
module MyServer
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    args = getargs(c)
    if :page in args
        write!(c, "requested page: " * args[:page])
    end
end

export home, logger
end
```
