`fegsymbol(S,p=0)`

returns as  a `CycPol` the  fake degree of  the character of symbol `S`.

```julia-repl
julia> fegsymbol([[1,5,6],[1,2]])
q¹⁶Φ₅Φ₇Φ₈Φ₉Φ₁₀Φ₁₁Φ₁₄Φ₁₆Φ₁₈Φ₂₀Φ₂₂
```

If `S` is an `e`-symbol, when given a second argument `p` dividing `e`, and a  first  argument  of  shape  `(0,…,0)`  representing  the  restriction of the character to `G(e,e,r)`, works for the coset `G(e,e,r).s₁ᵖ`.
