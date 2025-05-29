```
multiplicities(vectors; metric = EuclideanNorm(), atol = 1e-14, rtol = 1e-8, kwargs...)
```

Returns a `Vector{Vector{Int}}` `v`. Each vector `w` in 'v' contains all indices `i`,`j` such that `w[i]` and `w[j]` have `distance` at most `max(atol, rtol * metric(0,w[i]))`. The remaining `kwargs` are things that can be passed to [`UniquePoints`](@ref).

```julia-repl
julia> multiplicities([[1,0.5], [1,0.5], [1,1]])
[[1,2]]
```

This is the same as

```julia
multiplicities([[1,0.5], [1,0.5], [1,1]]; distance=(x,y) -> LinearAlgebra.norm(x-y))
```

Here is an example for using group actions.

```julia-repl
julia> X = [[1, 2, 3, 4], [2,1,3,4], [1,2,4,3], [2,1,4,3]]
julia> permutation(x) = [x[2], x[1], x[3], x[4]]
julia> m = multiplicities(X, group_action = permutation)
[[1,2], [3,4]]
```
