```
copy_tensor(;
    destination::DafWriter,
    source::DafReader,
    main_axis::AbstractString,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    [rows_reaxis::Maybe{AbstractString} = nothing,
    columns_reaxis::Maybe{AbstractString} = nothing,
    rename::Maybe{AbstractString} = nothing,
    dtype::Maybe{Type{<:StorageScalarBase}} = nothing,
    empty::Maybe{StorageScalar} = nothing,
    relayout::Bool = true,
    overwrite::Bool = false]
)::Nothing
```

テンソルをある `source` [`DafReader`](@ref) からある `destination` [`DafWriter`](@ref) にコピーします。

これは基本的に、`destination` の `main_axis` のエントリに基づいて、各テンソル行列に対して [`copy_matrix!`](@ref) を呼び出すループです。これは、ソースに存在しないがデスティネーションに存在するメイン軸のエントリに対して、`empty` 値で満たされた行列を作成します。
