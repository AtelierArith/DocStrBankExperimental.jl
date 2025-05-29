```julia
route!(c::AbstractConnection, r::AbstractRoute) -> ::Nothing
route!(c::Connection, tr::Routes{<:AbstractRoute}) -> ::Nothing
```

`route!` `Function` はルーターによって2回使用されます。1回目は全体の `Vector` のルートがルーティングされるとき（上記の2番目のメソッド）、2回目はルーティングされる `Route` に対してです。これを考慮すると、`route!(c::Connection, tr::Routes{<:AbstractRoute})` を拡張することで新しいルーターを作成することが可能です。以下の例は [`ChiProxy`](https://github.com/ChifiSource/ChiProxy.jl) から引き出されたもので、この例はホスト名に基づいてルーターを作成し、プロキシパスを実行するためにルート機能を変更します。

```julia
using Toolips
import Toolips: route!

function route!(c::Toolips.AbstractConnection, pr::AbstractProxyRoute)
    Toolips.proxy_pass!(c, "http://$(string(pr.ip4))")
end

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

  * 参照: `multiroute!`, `route!`, `Route`, `Routes`, `Connection`, `AbstractConnection`, `start!`
