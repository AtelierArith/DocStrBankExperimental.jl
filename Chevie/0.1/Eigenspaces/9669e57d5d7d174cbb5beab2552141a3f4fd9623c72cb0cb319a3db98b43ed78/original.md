`regular_eigenvalues(W)`

Let `W` be a reflection group or a reflection coset. A root of unity `ζ` is a *regular eigenvalue* for `W` if some element of `W` has a `ζ`-eigenvector which   lies   outside   of   the   reflecting  hyperplanes.  The  function returns the list of regular eigenvalues for `W`.

```julia-repl
julia> regular_eigenvalues(coxgroup(:G,2))
6-element Vector{Root1}:
   1
  -1
  ζ₃
 ζ₃²
  ζ₆
 ζ₆⁵

julia> W=complex_reflection_group(6)
G₆

julia> L=twistings(W,[2])[4]
G₆₍₂₎=G₃‚₁‚₁[ζ₄]Φ′₄

julia> regular_eigenvalues(L)
3-element Vector{Root1}:
    ζ₄
  ζ₁₂⁷
 ζ₁₂¹¹
```
