```
StorageMatrix{T} = AbstractMatrix{T} where {T <: StorageReal}
```

`Daf` ストレージから直接保存（および取得）できる行列。

要素の型は [`StorageReal`](@ref) でなければならず、ディスクファイルにデータを効率的に保存できるようにします。つまり、文字列の行列は **サポートされていません**。

!!! note
    保存するすべての行列は明確な [`MatrixLayouts`](@ref DataAxesFormats.MatrixLayouts) を持っている必要があり、行優先または列優先の形式でなければなりません。

