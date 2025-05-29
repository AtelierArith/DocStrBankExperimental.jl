```
insert!(as::AbstractSample, prop::Symbol, val)
```

サンプル `as` のメタデータにシンボル `prop` を使用して値 `val` を挿入します。`prop` が存在する場合はエラーが発生します。値が存在してもエラーを発生させたくない場合は、[`set!`](@ref) を使用してください。
