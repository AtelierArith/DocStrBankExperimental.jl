```
set!(commp::CommunityProfile, sample::AbstractString, prop::Symbol, val)
set!(commp::CommunityProfile, sample::AbstractString, md::Union{AbstractDict, NamedTuple})
```

コミュニティプロファイル `commp` のメタデータに、シンボル `prop` を使用して、サンプル `sample` の値 `val` を更新または挿入します。値がすでに存在する場合にエラーを発生させたい場合は、[`insert!`](@ref) を使用してください。

辞書またはキー=>値ペアを含む NamedTuple を渡すこともでき、すべてが `set!` されます。
