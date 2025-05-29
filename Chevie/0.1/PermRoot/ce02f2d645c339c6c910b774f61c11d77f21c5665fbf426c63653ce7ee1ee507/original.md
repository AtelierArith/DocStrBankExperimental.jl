`cartan(W::PermRootGroup)`    Cartan matrix of `W`.

Let  `s₁,…,sₙ` be reflections with associated  roots `rᵢ` and coroots `cᵢ`. The  matrix `C` with  entries `Cᵢ,ⱼ=cᵢ(rⱼ)` is  called a *Cartan matrix* of `s₁,…,sₙ`.  Since a reflection determines up to scalar a root and a coroot, `C`  is uniquely  determined by  `s₁,…,sₙ` up  to conjugation by a diagonal matrix.

If `s₁,…,sₙ` generate a reflection group `W`, then `C` up to conjugation by a  diagonal matrix is an invariant of the reflection representation of `W`. If invertible, the matrix `C` determines this representation since then the `rᵢ`  form a basis in  which the matrix for  `sᵢ` differs from the identity only  on  the  `i`-th  row,  where  the  corresponding  row of `C` has been subtracted.

In general `cartan(W)==simplecoroots(W)*permutedims(simpleroots(W))`.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> cartan(W)
3×3 Matrix{Int64}:
  2  -1   0
 -1   2  -1
  0  -1   2
```
