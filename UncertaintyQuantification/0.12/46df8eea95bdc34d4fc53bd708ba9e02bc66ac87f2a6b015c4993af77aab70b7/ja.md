```
evaluate!(ps::PolyharmonicSpline, df::DataFrame)
```

以前に構築されたPolyharmonicSplineメタモデルを使用して、与えられたデータを評価します。

#例

```jldoctest
julia> data = DataFrame(x = 1:10, y = [1, -5, -10, -12, -8, -1, 5, 12, 23, 50]);

julia> ps = PolyharmonicSpline(data, 2, :y);

julia> df = DataFrame( x = [2.5, 7.5, 12, 30]);

julia> evaluate!(ps, df);

julia> df.y |> DisplayAs.withcontext(:compact => true)
4-element Vector{Float64}:
  -7.75427
   8.29083
  84.4685
 260.437
```
