```
pearson_bounds(margins; n::Real=12, m::Real=128, kwargs...)
```

分布のリスト間の許容されるピアソン相関の範囲を決定します。

# フィールド

  * `margins`: 周辺分布のリスト。
  * `n`: 範囲を推定するために使用される多項式の次数。
  * `m`: エルミート多項式補間に使用される点の数。
  * `kwargs`: 追加のキーワード引数。現在は未使用。

# 例

```julia-repl
julia> using Distributions

julia> margins = [Exponential(3.14), NegativeBinomial(20, 0.2), LogNormal(2.718)];

julia> lower, upper = pearson_bounds(margins);

julia> lower
3×3 Matrix{Float64}:
  1.0       -0.855395  -0.488737
 -0.855395   1.0       -0.704403
 -0.488737  -0.704403   1.0

julia> upper
3×3 Matrix{Float64}:
 1.0       0.941367  0.939671
 0.941367  1.0       0.815171
 0.939671  0.815171  1.0
```
