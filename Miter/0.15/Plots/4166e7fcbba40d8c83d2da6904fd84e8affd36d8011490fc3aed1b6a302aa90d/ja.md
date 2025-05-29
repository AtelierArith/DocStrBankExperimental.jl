```julia
Circles(
    x_y_w,
    scale;
    stroke_color,
    stroke_width,
    fill_color
)

```

イテレータまたは `(x, y, w)` トリプレットのベクタを受け取り（例：`NTuple{3}`、ただし3つの要素を持つイテラブルなものであれば何でも可）、半径 `scale * √w` の円を `(x, y)` 座標を中心に描画します。

# キーワード引数

`stroke_color` はストロークの色を決定し、円をストロークしない場合は `nothing` を使用します。`stroke_width` は適用可能な場合のストロークの幅を決定します。

`fill_color` は円の塗りつぶしの色を決定します。
