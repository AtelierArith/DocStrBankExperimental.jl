`coxeter_matrix(m::AbstractMatrix)` または `coxmat`

は、カルタン行列 `m` によって定義されたコクセター群のコクセター行列を返します。

```julia-repl
julia> C=cartan(:H,3)
3×3 Matrix{Cyc{Int64}}:
       2  ζ₅²+ζ₅³   0
 ζ₅²+ζ₅³        2  -1
       0       -1   2

julia> coxmat(C)
3×3 Matrix{Int64}:
 1  5  2
 5  1  3
 2  3  1
```
