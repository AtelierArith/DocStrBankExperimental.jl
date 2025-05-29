```
same_axes(A, B...) -> axes(A)
```

配列 `A`、`B` などが同じ軸を持っているかどうかを確認し、それらを返します。軸がすべて同一でない場合は `DimensionMismatch` 例外がスローされます。

関連情報として [`same_size`](@ref)、[`all_indices`](@ref) を参照してください。
