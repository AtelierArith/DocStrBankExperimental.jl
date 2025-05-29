```
quiver3(x, y, z, u, v, w[, spec; kwargs...])
```

点 `(x,y,z)` で三次元ベクトル場を描画し、矢印のサイズは `(u,v,w)` です。

矢印の線のスタイルと色、そしてオプションで `(x,y,z)` 点に描画されるマーカーは、フォーマット文字列 `spec` とキーワード引数を通じて設定できます。これは [`plot`](@ref) や他の関数と同様です。

キーワード引数 `arrowscale` を使用して、矢印のサイズのスケールファクターを指定します。

!!! note
    2D [`quiver`](@ref) プロットの場合とは異なり、`quiver3` の3D矢印にはヘッドがありません。


# 例

```julia
# サンプルデータを作成
x = repeat(LinRange(-2, 2, 20), inner=10)
y = repeat(LinRange(0, pi, 10), outer=20)
z = sin.(x) .+ cos.(y)
u = 0.1ones(200)
v = zeros(200)
w = 0.5z
# ベクトルをプロット
quiver3(x, y, z, u, v, w, "o", markersize=0.5)

```
