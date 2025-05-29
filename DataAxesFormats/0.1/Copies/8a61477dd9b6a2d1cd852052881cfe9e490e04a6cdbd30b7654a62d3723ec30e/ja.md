```
copy_vector(;
    destination::DafWriter,
    source::DafReader,
    axis::AbstractString,
    name::AbstractString,
    [reaxis::Maybe{AbstractString} = nothing,
    rename::Maybe{AbstractString} = nothing,
    dtype::Maybe{Type{<:StorageScalarBase}} = nothing,
    default::Union{StorageScalar, StorageVector, Nothing, UndefInitializer} = undef,
    empty::Maybe{StorageScalar} = nothing,
    overwrite::Bool = false]
)::Nothing
```

ソース [`DafReader`](@ref) からデスティネーション [`DafWriter`](@ref) にベクトルをコピーします。

ベクトルは `axis`、`name`、および `default` を使用して取得されます。`reaxis` が指定されている場合、この軸を使用してベクトルを保存します。`rename` が指定されている場合、この名前を使用してベクトルを保存します。`dtype` が指定されている場合、データはこの型に変換されます。`overwrite`（デフォルトではない）が指定されている場合、ターゲット内の既存のベクトルを上書きします。

これには、1つのデータセットの軸がもう1つのデータセットの軸と同じであるか、またはそのスーパーセットまたはサブセットである必要があります。ターゲットの軸にソースに存在しないエントリが含まれている場合、`empty` を指定して欠損値を埋める必要があります。ソースの軸にターゲットに存在しないエントリが含まれている場合、それらは破棄されます（コピーされません）。
