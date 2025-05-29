```
savitskygolay(x, n, k, d=0)
savitskygolay(x, filter)
```

`x` に Savitsky-Golay フィルターを適用します。適用されるフィルターは、すでに計算された `filter` か、新たに計算された長さ `n`、次数 `k` および導関数の順序 `d` のフィルターです。

# 例

```jldoctest
julia> using Random

julia> x = -3π:0.1:3π;

julia> y = sin.(x) .+ randn(length(x));

julia> filtered = savitskygolay(y, 10, 2);

julia> size(filtered)
(158,)

julia> size(y)
(158,)

julia> filtered_derivative = savitskygolay(y, 10, 2, 1);

julia> size(filtered_derivative)
(158,)

```

参照: [`savitskygolayfilter`](@ref)
