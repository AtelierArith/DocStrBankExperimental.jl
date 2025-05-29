`YMatrix(W,w)`

Let  `W` be a finite reflection group on  the space `V` and let `w∈ W`. The function  `YMatrix` returns the  matrix of `w`  acting on the  dual `V*` of `V`.  This is the linear transformation of `V*` which acts trivially on the orthogonal  of the roots and has same  effect as `w` on the simple coroots. The function makes sense more generally for an element of the normalizer of `W`  in the whole permutation group of the coroots. The resulting matrix is the  transposed  of  the  matrix  `reflrep(W,w)`,  which,  according to our conventions  acts on the right (on the row vectors representing elements of the  dual of `V`). For  a `rootdatum` corresponding to  a coset `Wσ` we get the action of `Wσ` on `Y(𝐓)`.

```julia-repl
julia> W=reflection_subgroup(rootdatum("E7sc"),1:6)
E₇₍₁₂₃₄₅₆₎=E₆Φ₁

julia> YMatrix(W,longest(W))
7×7 transpose(::Matrix{Int64}) with eltype Int64:
  0   0   0   0   0  -1  0
  0  -1   0   0   0   0  0
  0   0   0   0  -1   0  0
  0   0   0  -1   0   0  0
  0   0  -1   0   0   0  0
 -1   0   0   0   0   0  0
  2   2   3   4   3   2  1
```
