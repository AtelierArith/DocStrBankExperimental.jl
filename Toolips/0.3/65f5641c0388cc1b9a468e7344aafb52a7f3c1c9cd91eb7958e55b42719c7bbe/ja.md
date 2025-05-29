```julia
get_post(c::AbstractConnection) -> ::String
```

現在の`Connection`の`POST`ボディを返します。

```example
module Server
using Toolips
logger = Toolips.Logger()

home = route("/") do c::Connection
    name = get_post(c)
    log(logger, "$name just posted")
    write!(c, "hello, $name")
end
export home, logger
end

using Toolips
start!(Server); println(Toolips.post("127.0.0.1":8000, "emmy"))
```
