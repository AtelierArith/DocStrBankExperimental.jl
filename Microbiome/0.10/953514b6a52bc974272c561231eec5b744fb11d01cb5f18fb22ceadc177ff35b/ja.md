```
set!(commp::CommunityProfile, sample::AbstractString, prop::Symbol, val)
set!(commp::CommunityProfile, sample::AbstractString, md::Union{AbstractDict, NamedTuple})
```

コミュニティプロファイル `commp` の `sample` のメタデータに値 `val` をシンボル `prop` を使って更新または挿入します。値がすでに存在する場合にエラーを発生させたい場合は、[`insert!`](@ref) を使用してください。

辞書またはキー=>値ペアを含む NamedTuple を渡すこともでき、すべてが `set!` されます。
