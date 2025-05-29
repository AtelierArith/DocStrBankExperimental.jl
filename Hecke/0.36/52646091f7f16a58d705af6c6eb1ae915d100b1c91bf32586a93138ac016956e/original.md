```
 divides(a::KInftyElem{T}, b::KInftyElem{T}, checked::Bool = true) where T <: FieldElement
```

Returns tuple `(flag, c)` where `flag = true` if $b$ divides $a$ and $a = bc$, otherwise `flag = false` and $c = 0$. If `checked = false` the corresponding element of the rational function field is returned and it is not checked whether it is an element of the given localization.
