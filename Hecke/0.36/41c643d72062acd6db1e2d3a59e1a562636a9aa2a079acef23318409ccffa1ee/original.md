```
 divides(a::OrdLocElem{T}, b::OrdLocElem{T}, checked::Bool = true) where {T <: AbsSimpleNumFieldElem}
```

Returns tuple (`true`,`c`) if $b$ divides $a$ where `c`*$b$ = $a$. If 'checked = false' the corresponding element of the numberfield is returned and it is not checked whether it is an element of the given localization.
