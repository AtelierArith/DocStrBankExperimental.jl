```
estimate(PValues, <:Pi0Estimator)
```

Estimate π₀, the fraction of tests under the null hypothesis

# Examples

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, StoreyBootstrap())
0.0
julia> estimate(pvals, FlatGrenander())
0.42553191489361697
```

# See also

`Pi0Estimator`s:

[`Storey`](@ref) [`StoreyBootstrap`](@ref) [`LeastSlope`](@ref) [`Oracle`](@ref) [`TwoStep`](@ref) [`RightBoundary`](@ref) [`CensoredBUM`](@ref) [`BUM`](@ref) [`FlatGrenander`](@ref) [`ConvexDecreasing`](@ref)
