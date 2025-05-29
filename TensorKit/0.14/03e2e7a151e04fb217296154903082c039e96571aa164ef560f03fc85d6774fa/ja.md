```
removeunit(P::HomSpace, i)
```

これは、位置 `1 ≤ i ≤ N` における自明なテンソル積因子を削除します。`i` は `Int` として指定することも、型の安定性を向上させるために `Val(i)` として指定することもできます。この操作が機能するためには、位置 `i` の空間がスカラーの体に同型である必要があります。

この操作は、[`insertleftunit`](@ref insertleftunit(::HomSpace, ::Val{i}) where {i}) および [`insertrightunit`](@ref insertrightunit(::HomSpace, ::Val{i}) where {i}) の作業を元に戻します。
