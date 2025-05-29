```
 divexact(a::KInftyElem{T}, b::KInftyElem{T}, checked::Bool = true)  where {T <: AbsSimpleNumFieldElem}
```

Returns element 'c' of given localization such that $a = bc$ if such element exists. If `checked = false` the corresponding element of the rational function field is returned and it is not checked whether it is an element of the given localization.
