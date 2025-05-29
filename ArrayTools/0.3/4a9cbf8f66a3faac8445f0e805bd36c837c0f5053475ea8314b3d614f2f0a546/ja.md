```
same_size(A, B...) -> size(A)
```

配列 `A`、`B` などがすべて同じサイズであるかどうかを確認し、そのサイズを返します。配列のサイズがすべて同一でない場合は、`DimensionMismatch` 例外がスローされます。

関連情報として [`same_standard_size`](@ref)、[`same_axes`](@ref) も参照してください。
