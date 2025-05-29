```
struct Route{T<:RouteRule, S<:Coordinate}
Route(rule, startpoint::Point{S}, endpoint::Point, start_direction, end_direction; waypoints=Point{S}[], waydirs=[])
Route(rule, path0::Path, endpoint::Point, end_direction)
```

`Route`は、指定された開始方向と終了方向を持つ2つの点の間に暗黙的に`Path`を定義します。

`Path(r::Route, sty::Paths.Style)`を使用して明示的なパスを作成します。

`Path`がどのように描画されるべきかを決定する`RouteRule`を含みます。

ルートを追加的に制約する`waypoints`と`waydirs`を含む場合があります。`RouteRule`はこれらがどのように処理されるかを決定し、デフォルトではウェイポイントからウェイポイントへのルーティングを行い、パスは`p0`から始まり、`waypoints`内の各点を順に通過し、最後に`p1`で終了します。

`waydirs`が`nothing`でない場合、`waypoints`と同じ長さである必要があります。`waydirs`が提供され、`RouteRule`によって無視されない場合（特定のルールのドキュメントを確認）、`waypoints[i]`は`waydirs[i]`に沿ってパスが向いている状態で到達します。
