```
 inv(a::OrdLocElem{T}, checked::Bool = true)  where {T <: AbsSimpleNumFieldElem}
```

Returns the inverse element of $a$ if $a$ is a unit. If 'checked = false' the invertibility of $a$ is not checked and the corresponding inverse element of the numberfield is returned.
