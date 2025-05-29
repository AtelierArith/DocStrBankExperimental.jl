`generic_order(W,q=Pol())`

returns  the generic  order of  `W` as  a polynomial  in `q` (the "compact" order  of the  Spets). This  is $q^{Nₕ}Πᵢ(q^{dᵢ}-1)$  where `dᵢ`  are the reflection  degrees and  `Nₕ` the  number of  reflecting hyperplanes. For a Weyl  group, it is the order  of the associated semisimple finite reductive group over the field with `q` elements.

```julia-repl
julia> PermRoot.generic_order(complex_reflection_group(4),Pol(:q))
Pol{Int64}: q¹⁴-q¹⁰-q⁸+q⁴
```
