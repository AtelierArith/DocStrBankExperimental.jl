```julia
get_args(c::AbstractConnection) -> ::Dict{Symbol, String}
```

現在の `Connection` の `GET` 引数を `Dict{Symbol, String}` で返します。

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
