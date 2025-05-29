```julia
route(::Function{T}, path::String) -> ::Route{T}
route(r::Route{<:AbstractConnection} ...) -> ::MultiRoute{Route{<:AbstractConnection}}
```

`route` `Function` は `Toolips` のデフォルトルートのルーティングインターフェースです。ほとんどの状況で `route` は *ターゲットパス* と `Function` を受け取り、これは `HTTP` レスポンスのハンドラーになります。この `Route` のハンドラー `Function` は、`AbstractConnection` のいくつかの型を受け取り、これを `MultiRoute` と一緒に使用するために注釈を付けることもできます。

ハンドラーの内部では、`Connection` にデータが `write!` で書き込まれます。これはデータ型と `Servables` の形で提供されます。`Servables` は、HTML やファイルを使ってウェブを構築するための基本的な構造であり、これには `Toolips` によって提供される `Component`、`File`、`Style`、および `KeyFrames` 型が含まれます。

```julia
module RoutingExample
using Toolips

desktop = route("/") do c::Connection
    write!(c, "このクライアントはデスクトップ上にいます")
end

mobile = route("/") do c::MobileConnection
    write!(c, "このクライアントはモバイル上にいます")
end

home = route(desktop, mobile)

export home
end
```

  * 参照: `multiroute!`, `route!`, `Route`, `Routes`, `Connection`, `AbstractConnection`, `start!`
