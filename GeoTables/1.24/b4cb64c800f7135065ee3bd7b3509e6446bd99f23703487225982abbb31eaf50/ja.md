```
@combine(geotable, :col₁ = expr₁, :col₂ = expr₂, ..., :colₙ = exprₙ)
```

ジオスペーシャル `geotable` を返し、列 `:col₁`, `:col₂`, ..., `:colₙ` が削減式 `expr₁`, `expr₂`, ..., `exprₙ` で計算されます。

`:geometry` 列に対して削減式が定義されていない場合、ジオメトリは `Multi` を使用して削減されます。

参照: [`@groupby`](@ref).

# 例

```julia
@combine(geotable, :x_sum = sum(:x))
@combine(geotable, :x_mean = mean(:x))
@combine(geotable, :x_mean = mean(:x), :geometry = centroid(:geometry))

groups = @groupby(geotable, :y)
@combine(groups, :x_prod = prod(:x))
@combine(groups, :x_median = median(:x))
@combine(groups, :x_median = median(:x), :geometry = centroid(:geometry))

@combine(geotable, {"z"} = sum({"x"}) + prod({"y"}))
xnm, ynm, znm = :x, :y, :z
@combine(geotable, {znm} = sum({xnm}) + prod({ynm}))
```
