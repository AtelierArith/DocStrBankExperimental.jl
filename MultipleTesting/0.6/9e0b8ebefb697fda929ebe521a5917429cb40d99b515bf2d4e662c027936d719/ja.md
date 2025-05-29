```
estimate(PValues, <:Pi0Estimator)
```

帰無仮説の下でのテストの割合であるπ₀を推定します

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, StoreyBootstrap())
0.0
julia> estimate(pvals, FlatGrenander())
0.42553191489361697
```

# 参照

`Pi0Estimator`s:

[`Storey`](@ref) [`StoreyBootstrap`](@ref) [`LeastSlope`](@ref) [`Oracle`](@ref) [`TwoStep`](@ref) [`RightBoundary`](@ref) [`CensoredBUM`](@ref) [`BUM`](@ref) [`FlatGrenander`](@ref) [`ConvexDecreasing`](@ref)
