```julia
get_method(c::AbstractConnection) -> ::String
```

受信した `HTTP` リクエストの `METHOD` を取得します。*METHOD* は、クライアントが送信しようとしている `HTTP` リクエストの種類であり、`POST` または `GET` です。

```example
module MyServer
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    @info "GET リクエストですか?: " * string(get_method(c) == "GET")
end

export home, logger
end
```
