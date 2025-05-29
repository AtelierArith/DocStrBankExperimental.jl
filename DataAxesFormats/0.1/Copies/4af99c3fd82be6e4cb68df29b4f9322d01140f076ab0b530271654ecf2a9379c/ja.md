```
copy_scalar(;
    destination::DafWriter,
    source::DafReader,
    name::AbstractString,
    [rename::Maybe{AbstractString} = nothing,
    dtype::Maybe{Type{<:StorageScalarBase}} = nothing,
    default::Union{StorageScalar, Nothing, UndefInitializer} = undef,
    overwrite::Bool = false]
)::Nothing
```

スカラーを、ある `source` [`DafReader`](@ref) からある `destination` [`DafWriter`](@ref) に `name` を使ってコピーします。

スカラーは `name` と `default` を使用して取得されます。`rename` が指定されている場合は、この新しい名前を使ってスカラーを保存します。`dtype` が指定されている場合、データはこの型に変換されます。`overwrite`（デフォルトではない）が指定されている場合、ターゲット内の既存のスカラーを上書きします。
