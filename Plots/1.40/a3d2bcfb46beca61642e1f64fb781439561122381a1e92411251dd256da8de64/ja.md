```
quiver(x,y,quiver=(u,v))
quiver!(x,y,quiver=(u,v))
```

ベクトル場（クイバ）プロットを作成します。`i`番目のベクトルは、`(x[i],y[i])`から`(x[i] + u[i], y[i] + v[i])`まで伸びます。

# キーワード引数

  * `arrow::Union{Bool, Plots.Arrow}`: パスラインセグメントの終わりに表示されるべき矢印の先端を定義します（NaNの直前と最後の非NaNポイントの直前）。quiverplot、streamplot、またはそれに類似したものに使用されます。エイリアス: (:arrows,).

# 例

```julia-repl
julia> quiver([1,2,3],[3,2,1],quiver=([1,1,1],[1,2,3]))
```
