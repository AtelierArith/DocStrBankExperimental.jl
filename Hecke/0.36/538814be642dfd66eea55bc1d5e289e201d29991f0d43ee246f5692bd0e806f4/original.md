```
 divexact(a::OrdLocElem{T}, b::OrdLocElem{T}, checked::Bool = true)  where {T <: AbsSimpleNumFieldElem}
```

Returns element 'c' of given localization s.th. `c`*$b$ = $a$ if such element exists. If 'checked = false' the corresponding element of the numberfield is returned and it is not checked whether it is an element of the given localization.
