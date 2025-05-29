```
unset!(as::AbstractSample, prop::Symbol)
```

サンプル `as` のメタデータエントリをシンボル `prop` を使用して削除します。値が存在しない場合にエラーをスローさせたい場合は、[`delete!`](@ref) を使用してください。
