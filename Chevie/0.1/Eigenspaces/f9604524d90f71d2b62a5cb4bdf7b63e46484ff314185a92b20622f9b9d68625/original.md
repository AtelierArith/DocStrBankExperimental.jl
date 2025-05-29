`eigenspace_projector(WF,w,ζ::Root1=1)`

Let `WF` be a reflection group or a reflection coset, let `w` be an element of  `WF` and let  `ζ` be a  root of unity.  The function returns the unique `w`-invariant projector on the `ζ`-eigenspace of `w`.

The  eigenvalue `ζ` can also  be specified by giving  an integer `d` (which then  specifies  `ζ=E(d)`)  or  a  fraction  `a//b`  which  then  specifies `ζ=E(b,a)`. If omitted, `ζ` is taken to be `1`.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> w=W(1:3...)
(1,12,3,2)(4,11,10,5)(6,9,8,7)

julia> p=eigenspace_projector(W,w,1//4)
3×3 Matrix{Cyc{Rational{Int64}}}:
  (1+ζ₄)/4   ζ₄/2  (-1+ζ₄)/4
  (1-ζ₄)/4   1//2   (1+ζ₄)/4
 (-1-ζ₄)/4  -ζ₄/2   (1-ζ₄)/4

julia> GenLinearAlgebra.rank(p)
1
```
