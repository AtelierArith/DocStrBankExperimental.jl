```
rewrite_match_maps(r::Rule{:SqPO},m; pres::Union{Nothing, Presentation}=nothing)
```

Sesqui-pushout is just like DPO, except we use a final pullback complement instead of a pushout complement.

```
r.L  r.R
```

L <-⌞K -> R m ↓    ↓k   ↓ r   I <- • ->⌜O      i   o
