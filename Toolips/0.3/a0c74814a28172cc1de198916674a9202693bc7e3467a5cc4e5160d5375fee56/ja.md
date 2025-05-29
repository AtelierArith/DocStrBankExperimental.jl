```julia
log(c::Connection, message::String, at::Int64 = 1) -> ::Nothing
```

`log`は、あなたの`Logger`を使用して`at`のクレヨンでメッセージを印刷します。`Logger`はこれに関してもっと多くの情報を提供します。

```example
module MyServer
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    log(c, "hello server!")
    write!(c, "hello client!")
end

export home, logger
end
```
