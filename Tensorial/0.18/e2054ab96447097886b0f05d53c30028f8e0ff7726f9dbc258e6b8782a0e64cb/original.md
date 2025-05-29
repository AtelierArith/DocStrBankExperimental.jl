```
tomandel(A::Union{SymmetricSecondOrderTensor, SymmetricFourthOrderTensor})
```

Convert a tensor to Mandel form which is equivalent to `tovoigt(A, offdiagscale = √2)`.

See also [`tovoigt`](@ref).
