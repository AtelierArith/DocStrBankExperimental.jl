```
StorageVector{T} = AbstractVector{T} where {T <: StorageScalar}
```

`Daf` ストレージから直接保存（および取得）できるベクトル。

要素の型は [`StorageScalar`](@ref) でなければならず、ディスクファイルにデータを保存できるようにします。文字列のベクトルもサポートされていますが、効率は低下します。
