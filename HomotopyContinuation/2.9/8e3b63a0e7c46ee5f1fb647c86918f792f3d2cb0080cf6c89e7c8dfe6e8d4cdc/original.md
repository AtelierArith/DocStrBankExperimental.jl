```
permutations(r::MonodromyResult; reduced=true)
```

Return the permutations of the solutions that are induced by tracking over the loops. If `reduced=false`, then all permutations are returned. If `reduced=true` then permutations without repetitions are returned.

If a solution was not tracked in the loop, then the corresponding entry is 0.

Example: monodromy loop for a varying line that intersects two circles.

```julia
using LinearAlgebra
@var x[1:2] a b c
c1 = (x - [2, 0]) ⋅ (x - [2, 0]) - 1
c2 = (x - [-2, 0]) ⋅ (x - [-2, 0]) - 1
F = [c1 * c2; a * x[1] + b * x[2] - c]
S = monodromy_solve(F, [[1, 0]], [1, 1, 1], parameters = [a, b, c], permutations = true)

permutations(S)
```

will return

```julia
2×2 Array{Int64,2}:
 1  2
 2  1
```

and `permutations(S, reduced = false)` returns

```julia
2×12 Array{Int64,2}:
 1  2  2  1  1  …  1  2  1  1  1
 2  1  1  2  2     2  1  2  2  2
```
