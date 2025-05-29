```
serve(server::WebsocketServer, [port::Int, host::String; options...])
```

TCP接続リスナーを開きます。サーバーがリスニングしている間はブロックします。

デフォルト:

  * port: 8080
  * host: "localhost"

`; options...` は基盤となる [HTTP.servers.listen](https://juliaweb.github.io/HTTP.jl/v1.0.2/server/#HTTP.listen) に渡されます。

# 例

```julia
closed = Condition()
#...
@async serve(server, 8081, "localhost")
#...
wait(closed)
```
