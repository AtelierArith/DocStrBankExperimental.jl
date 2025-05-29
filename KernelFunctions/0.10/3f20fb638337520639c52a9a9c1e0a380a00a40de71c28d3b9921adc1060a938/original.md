```
median_heuristic_transform(distance, x::AbstractVector)
```

Create a [`ScaleTransform`](@ref) that divides the input elementwise by the median `distance` of the data points in `x`.

The `distance` has to support pairwise evaluation with `KernelFunctions.pairwise`. All `PreMetric`s of the package [Distances.jl](https://github.com/JuliaStats/Distances.jl) such as `Euclidean` satisfy this requirement automatically.

# Examples

```jldoctest
julia> using Distances, Statistics

julia> x = ColVecs(rand(100, 10));

julia> t = median_heuristic_transform(Euclidean(), x);

julia> y = map(t, x);

julia> median(euclidean(y[i], y[j]) for i in 1:10, j in 1:10 if i != j) ≈ 1
true
```
