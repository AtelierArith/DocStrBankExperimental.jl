```
copy_matrix(;
    destination::DafWriter,
    source::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    [rows_reaxis::Maybe{AbstractString} = nothing,
    columns_reaxis::Maybe{AbstractString} = nothing,
    rename::Maybe{AbstractString} = nothing,
    dtype::Maybe{Type{<:StorageScalarBase}} = nothing,
    default::Union{StorageScalar, StorageVector, Nothing, UndefInitializer} = undef,
    empty::Maybe{StorageScalar} = nothing,
    relayout::Bool = true,
    overwrite::Bool = false]
)::Nothing
```

ある `source` [`DafReader`](@ref) から別の `destination` [`DafWriter`](@ref) に行列をコピーします。

行列は `rows_axis`、`columns_axis`、`name`、`relayout`、および `default` を使用して取得されます。`rows_reaxis` および/または `columns_reaxis` が指定されている場合、これらの軸を使用してベクトルを保存します。`rename` が指定されている場合、この名前を使用して行列を保存します。`dtype` が指定されている場合、データはこの型に変換されます。`overwrite`（デフォルトではない）が指定されている場合、ターゲット内の既存の行列を上書きします。行列は同じ `relayout` で保存されます。

これには、1つのデータセットの各軸が同じであるか、または他のデータセットのスーパーセットまたはサブセットである必要があります。ターゲット軸にソースに存在しないエントリが含まれている場合、`empty` を指定して欠損値を埋める必要があります。ソース軸にターゲットに存在しないエントリが含まれている場合、それらは破棄されます（コピーされません）。

!!! note
    サブセットからスーパーセットに行列をコピーする際、`empty` 値がゼロの場合、ターゲットにスパース行列を作成します。しかし、現在はこれに対して一時的な密行列を作成しています。これは非効率的であり、より効率的な方法に置き換えるべきです。

