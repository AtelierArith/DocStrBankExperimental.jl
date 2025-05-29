```
frommandel(S::Type{<: Union{SymmetricSecondOrderTensor, SymmetricFourthOrderTensor}}, A::AbstractArray{T})
```

Create a tensor of type `S` from Mandel form. This is equivalent to `fromvoigt(S, A, offdiagscale = √2)`.

See also [`fromvoigt`](@ref).
