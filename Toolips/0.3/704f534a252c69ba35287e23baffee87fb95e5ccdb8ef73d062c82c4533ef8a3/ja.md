```julia
get_host(c::AbstractConnection) -> ::String
```

クライアントが現在リクエストしているホスト（ドメイン名とTLD）を取得します。以下の例は、[`ChiProxy`](https://github.com/ChifiSource/ChiProxy.jl) から直接引き出されたものです。これは、ターゲットではなくホスト名に基づいたルーターを使用する `Toolips` ベースのプロキシサーバーです。プロキシルートでの動作を変更するために `route!` を拡張することで、この例では `get_route` ではなく `get_host` を使用してアクティブなパスを決定します。

```example
using Toolips
import Toolips: route!
route!(c::Connection, vec::Vector{<:AbstractProxyRoute}) = begin
    if Toolips.get_route(c) == "/favicon.ico"
        write!(c, "no icon here, fool")
        return
    end
    selected_route::String = get_host(c)
    if selected_route in vec
        route!(c, vec[selected_route])
    else
        write!(c, "this route is not here")
    end
end
```
