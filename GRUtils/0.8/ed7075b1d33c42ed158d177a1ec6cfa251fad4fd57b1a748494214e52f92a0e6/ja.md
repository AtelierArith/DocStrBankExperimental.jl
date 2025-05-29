```
quiver(x, y, u, v[, spec; kwargs...])
```

点 `(x,y)` でベクトル場を描画し、矢印のサイズは `(u,v)` です。

矢印の線のスタイルと色、そしてオプションで `(x,y)` 点に描かれるマーカーは、フォーマット文字列 `spec` とキーワード引数を通じて設定できます。これは [`plot`](@ref) や他の関数と同様です。

キーワード引数 `arrowscale` と `headsize` を使用して、矢印とその頭のサイズのスケールファクターを指定します。

# 例

```julia
# サンプルデータを作成
x = repeat(LinRange(-2, 2, 20), inner=10)
y = repeat(LinRange(-1, 1, 10), outer=20)
u = x .* (x.^2 .+ y.^2)
v = y .* (x.^2 .+ y.^2)
# 矢印をプロット
quiver(x, y, u, y, arrowscale=0.1)
# 矢印全体を見るためにy軸を拡張
ylim(-1.15, 1.15)

```
