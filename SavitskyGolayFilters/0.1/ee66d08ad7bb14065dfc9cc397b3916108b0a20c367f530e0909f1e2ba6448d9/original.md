```
savitskygolay(x, n, k, d=0)
savitskygolay(x, filter)
```

Apply a Savitsky-Golay filter on `x`. The applied filter is either the already calculated `filter` or a newly calculated filter of length `n`, degree `k`  and derivative order `d`.

# Examples

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

See also: [`savitskygolayfilter`](@ref)
