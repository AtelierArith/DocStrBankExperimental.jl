```
real_solutions(result; tol=1e-6, conditions...)
```

与えられた条件が適用されるすべての実数解を返します。可能な `conditions` については [`results`](@ref) を参照してください。`only_real` は常に `true` であり、`real_tol` は現在 `tol` です。

## 例

```julia-repl
julia> @var x y;
julia> F = System([(x-2)y, y+x+3]);
julia> real_solutions(solve(F))
2-element Array{Array{Float64,1},1}:
 [2.0, -5.0]
 [-3.0, 0.0]
```
