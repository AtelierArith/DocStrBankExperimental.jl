```julia
get_parent(c::AbstractConnection) -> ::String
```

Returns the `parent`, which might reference where a browser is navigating from.

```example
module MyServer
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    log(logger, get_parent(c))
    write!(c, "c:")
end
export home
end
```
