```
bestify(
    matrix::AbstractMatrix{T};
    copy::Bool = false,
    sparse_if_saves_storage_fraction::AbstractFloat = 0.25,
)::AbstractMatrix{T} where {T <: StorageReal}
bestify(
    matrix::AbstractVector{T};
    copy::Bool = false,
    sparse_if_saves_storage_fraction::AbstractFloat = 0.25,
)::AbstractVector{T} where {T <: StorageReal}
```

配列の「最適な」（密または疎）バージョンを返します。疎形式は、密形式のストレージの少なくとも`sparse_if_saves_storage_fraction`を節約できる場合に選択されます。`copy`が指定されている場合、最適な形式であってもコピーが作成されます。

!!! note
    `copy`が指定されていない場合、行列がすでに疎であれば、スペースを節約できる場合でも整数インデックスの型は変更しません。

