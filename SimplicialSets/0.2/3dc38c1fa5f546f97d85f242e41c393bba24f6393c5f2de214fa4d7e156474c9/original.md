```
Tuple(x::ProductSimplex{T}) where T -> T <: Tuple{Vararg{AbstractSimplex}}
components(x::ProductSimplex{T}) where T -> T <: Tuple{Vararg{AbstractSimplex}}
```

Return the tuple of component simplices of `x`.

!!! note
    The function `components` is deprecated. Use `Tuple` instead.

