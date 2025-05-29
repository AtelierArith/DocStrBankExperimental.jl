`gendeg_symbol(S)`

returns  as  a  `CycPol`  the  generic  degree  of  the unipotent character parameterized by `S`.

```julia-repl
julia> gendeg_symbol([[1,2],[1,5,6]])
q¹³Φ₅Φ₆Φ₇Φ₈²Φ₉Φ₁₀Φ₁₁Φ₁₄Φ₁₆Φ₁₈Φ₂₀Φ₂₂/2
```

for an `e`-symbol of rank `r`, content `c` and Malle-defect `d` the Spets is

  * G(e,1,r) (c==1, d==0)
  * G(e,e,r) (c==0, d==0)
  * ²G(e,e,r) (c==0, d==1) (e,r even. This includes ²Dₙ, ²B₂, ²G₂)

see [3.9 and 6.4 Malle1995](biblio.htm#Mal95).
