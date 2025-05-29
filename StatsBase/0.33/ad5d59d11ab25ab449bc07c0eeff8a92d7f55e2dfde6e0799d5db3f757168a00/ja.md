```
standardize(DT, X; dims=nothing, kwargs...)
```

変換 `DT`（`AbstractDataTransform` のサブタイプ）を使用して、次元 `dims` に沿ったベクトルまたは行列 `X` の標準化されたコピーを返します：

  * `ZScoreTransform`
  * `UnitRangeTransform`

# 例

```jldoctest
julia> using StatsBase

julia> standardize(ZScoreTransform, [0.0 -0.5 0.5; 0.0 1.0 2.0], dims=2)
2×3 Matrix{Float64}:
  0.0  -1.0  1.0
 -1.0   0.0  1.0

julia> standardize(UnitRangeTransform, [0.0 -0.5 0.5; 0.0 1.0 2.0], dims=2)
2×3 Matrix{Float64}:
 0.5  0.0  1.0
 0.0  0.5  1.0
```
