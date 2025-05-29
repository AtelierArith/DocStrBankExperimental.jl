`cartan(M::AbstractMatrix)` Cartan matrix from Coxeter matrix

The  argument should be the Coxeter matrix  `M` for a Coxeter group `W` and the   result  is  the  Cartan  Matrix   `C`  for  the  standard  reflection representation  of `W`. We have `C[s,t]=-2cos(π/M[s,t])`, where `M[s,s]==1` and  by  convention  `π/M[s,t]==0`  if  `M[s,t]==∞`,  which we represent by `M[s,t]==0`.  Since  `M`  is  symmetric,  the  resulting  `C` is symmetric, meaning  that all roots  in the constructed  reflection representation have same length.

```julia-repl
julia> cartan([1 3;3 1])
2×2 Matrix{Cyc{Int64}}:
  2  -1
 -1   2
```
