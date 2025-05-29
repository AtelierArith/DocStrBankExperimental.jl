```
npa2sdp(expr, level; eq=[], ge=[])
```

Generate the NPA relaxation for a given quantum optimisation problem, at the indicated level of the NPA hierarchy.

This basically uses the `npa_moment` function to generate the moment matrix and then calls `npa2sdp` again with the moment matrix as the second argument, which takes the real part of the problem and then eliminates the equality constraints by substitution.

# Example

```julia-repl
julia> S = A1*(B1 + B2) + A2*(B1 - B2)
A1 B1 + A1 B2 + A2 B1 - A2 B2

julia> (objective, moments) = npa2sdp(S, 1, eq=[A2*B1 - Id]);

julia> objective
Id + A1 B1 + A1 B2 - A2 B2

julia> moments[1][Id]
5×5 SparseArrays.SparseMatrixCSC{Float64, Int64} with 7 stored entries:
 1.0   ⋅    ⋅    ⋅    ⋅
  ⋅   1.0   ⋅    ⋅    ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅    ⋅    ⋅   1.0

julia> QuantumNPA.repack(moments[1])
5×5 Matrix{Polynomial}:
 Id  A1     A2     B1     B2
 A1  Id     A1 A2  A1 B1  A1 B2
 A2  A1 A2  Id     Id     A2 B2
 B1  A1 B1  Id     Id     B1 B2
 B2  A1 B2  A2 B2  B1 B2  Id
```
