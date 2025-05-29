```
removeunit(tsrc::AbstractTensorMap, i; copy=false) -> tdst
```

これは、位置 `1 ≤ i ≤ N` にある自明なテンソル積因子を削除します。`i` は `Int` または型の安定性を向上させるために `Val(i)` として指定できます。この操作が機能するためには、その因子がスカラーの体と同型である必要があります。

`copy=false` の場合、`tdst` は可能な限り `tsrc` とデータを共有することがあります。そうでない場合、常にコピーが作成されます。

この操作は、[`insertleftunit`](@ref insertleftunit(::AbstractTensorMap, ::Val{i}) where {i}) および [`insertrightunit`](@ref insertrightunit(::AbstractTensorMap, ::Val{i}) where {i}) の作業を元に戻します。
