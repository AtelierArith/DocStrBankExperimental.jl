```
curves(x,y)
curves!(x,y)
```

点 `(x[1],y[1])` から `(x[end],y[end])` まで、制御点 `(x[2],y[2]), ..., (x[end-1],y[end]-1)` を持つベジェ曲線を描画します。

# キーワード引数

  * `fillrange::Union{Real, AbstractVector}`: 線の種類の場合、`fillrange` と `y` の間の領域を塗りつぶし、`bar`、`sticks` タイプの基準を設定し、他のタイプに対しても同様です。エイリアス: (:fill_between, :fillbetween, :fillranges, :fillrng, :fillto, :frange)。

# 例

```julia-repl
julia> curves([1,2,3,4],[1,1,2,4])
```
