`reflection_representation(W::ComplexReflectionGroup,w)` or `reflrep(W,w)`

Let  `V` be the space on  which `W` acts as a  reflection group and let `w∈ W`,  represented  as  a  permutation  of  the roots. The function `reflrep` returns  the matrix of `w` acting on  `V` (*from the right* on the elements of  `V` seen as  row vectors by  our conventions in  `Chevie`). This is the linear  transformation of `V` which acts trivially on the orthogonal of the coroots  and has same effect as `w` on the simple roots. The function makes sense  more generally for a permutation of  the roots induced by an element of  `GL(V)` which stabilizes the roots (thus in particular normalizes `W`); thus  it works for reflection cosets.  For a `rootdatum` corresponding to a coset `Wσ` we get the action of `Wσ` on `X(𝐓)`.

```julia-repl
julia> W=reflection_subgroup(rootdatum("E7sc"),1:6)
E₇₍₁₂₃₄₅₆₎=E₆Φ₁

julia> reflrep(W,longest(W))
7×7 Matrix{Int64}:
  0   0   0   0   0  -1  2
  0  -1   0   0   0   0  2
  0   0   0   0  -1   0  3
  0   0   0  -1   0   0  4
  0   0  -1   0   0   0  3
 -1   0   0   0   0   0  2
  0   0   0   0   0   0  1
```
