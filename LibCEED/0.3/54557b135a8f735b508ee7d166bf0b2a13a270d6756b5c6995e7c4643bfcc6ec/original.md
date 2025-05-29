```
setvoigt(J::StaticArray{Tuple{D,D},T,2})
setvoigt(J, ::CeedDim{dim})
```

Given a symmetric matrix `J`, return a `SVector` that encodes `J` using the [Voigt convention](https://en.wikipedia.org/wiki/Voigt_notation).

The size of the symmetric matrix `J` must be known statically, either specified using [`CeedDim`](@ref) or `StaticArray`.
