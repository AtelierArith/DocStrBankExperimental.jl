```julia
proxy_pass!(c::AbstractConnection, url::String) -> ::Nothing
```

*プロキシパス*を実行します - クライアントを別のサーバーにリダイレクトし、リクエストを実行することなく、現在のサーバーを*プロキシ*として使用して他のサーバーにサービスを提供します。

```example
module MyServer
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    proxy_pass!(c, "https://github.com/ChifiSource")
end

export home, logger
end
```
