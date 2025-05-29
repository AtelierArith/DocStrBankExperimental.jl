```
removeunit(P::ProductSpace, i::Int)
```

これは、位置 `1 ≤ i ≤ N` にある自明なテンソル積因子を削除します。`i` は `Int` または型の安定性を向上させるために `Val(i)` として指定できます。この操作が機能するためには、その因子がスカラーの体と同型である必要があります。

この操作は、[`insertleftunit`](@ref insertleftunit(::ProductSpace, ::Val{i}) where {i}) および [`insertrightunit`](@ref insertrightunit(::ProductSpace, ::Val{i}) where {i}) の作業を元に戻します。
