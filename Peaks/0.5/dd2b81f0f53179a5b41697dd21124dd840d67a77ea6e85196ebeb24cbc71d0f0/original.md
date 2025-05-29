```
simplemaxima(x) -> Vector{Int}
```

Find the indices of local maxima in `x`, where each maxima `i` is greater than both adjacent elements or is the first index of a plateau.

A plateau is defined as a maxima with consecutive equal (`==`) maximal values which are bounded by lesser values immediately before and after the plateau.

This function is semantically equivalent to `argmaxima(x, w=1; strict=true)`, but is faster because of its simplified set of features. (The difference in speed scales with `length(x)`; for input arrays longer than 5k elements, `argmaxima` is roughly 7x slower.)

Vectors with `missing`s are not supported by `simplemaxima`, use `argmaxima` if this is needed.

See also: [`argmaxima`](@ref)

# Examples

```julia-repl
julia> simplemaxima([0,2,0,1,1,0])
2-element Vector{Int64}:
 2
 4

julia> argmaxima([0,2,0,1,1,0])
2-element Vector{Int64}:
 2
 4

julia> simplemaxima([2,0,1,1])
Int64[]

julia> @btime simplemaxima(x) setup=(x = repeat([0,1]; outer=100));
  269.865 ns (3 allocations: 1.00 KiB)

julia> @btime argmaxima(x) setup=(x = repeat([0,1]; outer=100));
  748.780 ns (3 allocations: 1.00 KiB)
```
