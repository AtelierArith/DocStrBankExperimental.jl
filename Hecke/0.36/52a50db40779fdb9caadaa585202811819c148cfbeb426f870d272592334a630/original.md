```
 inv(a::KInftyElem{T}, checked::Bool = true)  where T <: FieldElement
```

Returns the inverse element of $a$ if $a$ is a unit. If 'checked = false' the invertibility of $a$ is not checked and the corresponding inverse element of the rational function field is returned.
