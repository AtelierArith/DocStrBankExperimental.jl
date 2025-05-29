`CorranPicantinMonoid(e,n,k=1)`

returns the interval monoid defined by G. Neaime, http://arxiv.org/abs/1707.06864,   which  generalizes  the  Corran-Picantin monoid for `G(e,e,n)`.

In  this monoid `δ` has `image`  the element of `G(e,e,n)` corresponding to the  diagonal matrix whose  diagonal entries except  the first are equal to `E(e)^k`;  this  monoid  is  isomorphic  to  the Corran-Picantin monoid for `G(e,e,n)` when `gcd(k,e)=1`.

```julia-repl
julia> C=CorranPicantinMonoid(3,3)
CorranPicantinMonoid(3,3,3)

julia> word(C(C.δ))
6-element Vector{Int64}:
 1
 3
 4
 1
 3
 4

julia> Matrix(C,C.δ)
3×3 Matrix{Cyc{Int64}}:
 ζ₃   0   0
  0  ζ₃   0
  0   0  ζ₃

julia> b=C(1,2,3,4)^3
1.2.341.2.341.2.34

julia> Matrix(C,b[3])
3×3 Matrix{Cyc{Int64}}:
 0    0  ζ₃
 0  ζ₃²   0
 1    0   0
```

© July 2017 –- Jean Michel and Georges Neaime
