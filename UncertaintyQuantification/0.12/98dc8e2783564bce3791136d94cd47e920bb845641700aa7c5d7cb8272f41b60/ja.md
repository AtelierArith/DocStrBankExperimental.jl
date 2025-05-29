```
evaluate!(rs::ResponseSurface, data::DataFrame)
```

以前に訓練されたResponseSurfaceを使用してデータを評価します。

# 例

```jldoctest
julia> data = DataFrame(x = 1:10, y = [1, 4, 10, 15, 24, 37, 50, 62, 80, 101]);

julia> rs = ResponseSurface(data, :y, 2);

julia> df = DataFrame(x = [2.5, 11, 15]);

julia> evaluate!(rs, df);

julia> df.y |> DisplayAs.withcontext(:compact => true)
3-element Vector{Float64}:
   6.25511
 121.15
 226.165
```
