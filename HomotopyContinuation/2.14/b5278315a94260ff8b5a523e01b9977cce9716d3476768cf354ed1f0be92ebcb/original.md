```
real_solutions(result; tol=1e-6, conditions...)
```

Return all real solution for which the given conditions apply. For the possible `conditions` see [`results`](@ref). Note that `only_real` is always `true` and `real_tol` is now `tol`.

## Example

```julia-repl
julia> @var x y;
julia> F = System([(x-2)y, y+x+3]);
julia> real_solutions(solve(F))
2-element Array{Array{Float64,1},1}:
 [2.0, -5.0]
 [-3.0, 0.0]
```
