`deligne_lusztig_character(W,w)` or `dlchar(W,w)`

This  function returns the Deligne-Lusztig character  $R_𝐓 ^𝐆 (1)$ of the algebraic  group `𝐆` associated to the Coxeter group or Coxeter coset `W`. The  torus  `𝐓`  can  be  specified  in  3  ways:  if `w` is an integer, it represents the `w`-th conjugacy class (or `phi`-conjugacy class for a coset `Wϕ`)  of `W`. Otherwise  `w` can be  a word or  an element of  `W`, and it represents the class (or `ϕ`-class) of `w`.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> dlchar(W,3)
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>

julia> dlchar(W,W(1))
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>

julia> dlchar(W,[1])
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>

julia> dlchar(W,[1,2])
[G₂]:<φ₁‚₀>+<φ₁‚₆>-<φ₂‚₁>+<G₂[-1]>+<G₂[ζ₃]>+<G₂[ζ₃²]>
```
