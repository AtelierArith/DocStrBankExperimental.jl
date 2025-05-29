```
insert!(commp::CommunityProfile, sample::AbstractString, prop::Symbol, val)
```

コミュニティプロファイル `commp` の `sample` のメタデータに値 `val` をシンボル `prop` を使って挿入します。`prop` が存在する場合はエラーが発生します。値が存在してもエラーを発生させたくない場合は、[`set!`](@ref) を使用してください。
