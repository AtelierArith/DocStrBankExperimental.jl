`FFE{p}(z::Cyc)`  where `z` is  a `p`-integral cyclotomic  number (that is, `z`  times some number prime  to `p` is a  cyclotomic integer), returns the reduction  of `z` mod.  `p`, an element  of some extension  `𝔽_{pʳ}` of the prime field `𝔽ₚ`.

```julia_repl
julia> FFE{3}(E(7))
Z₇₂₉¹⁰⁴
```
