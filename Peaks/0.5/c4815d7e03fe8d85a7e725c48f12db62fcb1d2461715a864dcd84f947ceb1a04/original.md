```
simpleminima(x) -> Vector{Int}
```

Find the indices of local minima in `x`, where each minima `i` is less than both adjacent elements or is the first index of a plateau.

A plateau is defined as a minima with consecutive equal (`==`) minimal values which are bounded by greater values immediately before and after the plateau.

This function is semantically equivalent to `argminima(x, w=1; strict=true)`, but is faster because of its simplified set of features. (The difference in speed scales with `length(x)`; for input arrays longer than 5k elements, `argmaxima` is roughly 7x slower.)

Vectors with `missing`s are not supported by `simpleminima`, use `argminima` if this is needed.

See also: [`argminima`](@ref)

# Examples

```julia-repl
julia> simpleminima([3,2,3,1,1,3])
2-element Vector{Int64}:
 2
 4

julia> argminima([3,2,3,1,1,3])
2-element Vector{Int64}:
 2
 4

julia> simpleminima([2,3,1,1])
Int64[]

julia> @btime simpleminima(x) setup=(x = repeat([0,1]; outer=100));
  280.362 ns (3 allocations: 1.00 KiB)

julia> @btime argminima(x) setup=(x = repeat([0,1]; outer=100));
  823.634 ns (3 allocations: 1.00 KiB)
```
