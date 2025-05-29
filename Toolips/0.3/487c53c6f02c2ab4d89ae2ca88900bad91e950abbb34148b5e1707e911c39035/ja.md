```julia
get_parent(c::AbstractConnection) -> ::String
```

`parent`を返します。これは、ブラウザがどこからナビゲートしているかを参照している可能性があります。

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
