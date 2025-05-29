```
solutions(result; only_nonsingular = true, conditions...)
```

与えられた条件が適用されるすべての解を返します。可能な条件については[`results`](@ref)を参照してください。

## 例

```julia-repl
julia> @var x y
julia> F = System([(x-2)y, y+x+3]);
julia> solutions(solve(F))
2-element Array{Array{Complex{Float64},1},1}:
 [2.0 + 0.0im, -5.0 + 0.0im]
 [-3.0 + 0.0im, 0.0 + 0.0im]
```
