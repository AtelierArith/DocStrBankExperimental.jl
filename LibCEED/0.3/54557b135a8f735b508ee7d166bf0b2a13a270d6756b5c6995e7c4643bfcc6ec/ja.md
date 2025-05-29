```
setvoigt(J::StaticArray{Tuple{D,D},T,2})
setvoigt(J, ::CeedDim{dim})
```

対称行列 `J` が与えられたとき、[Voigt convention](https://en.wikipedia.org/wiki/Voigt_notation) を使用して `J` をエンコードする `SVector` を返します。

対称行列 `J` のサイズは静的に知られている必要があり、[`CeedDim`](@ref) または `StaticArray` を使用して指定されます。
