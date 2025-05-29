```
set!(as::AbstractSample, prop::Symbol, val)
```

サンプル `as` のメタデータにシンボル `prop` を使用して値 `val` を更新または挿入します。値がすでに存在する場合にエラーを発生させたい場合は、[`insert!`](@ref) を使用してください。
