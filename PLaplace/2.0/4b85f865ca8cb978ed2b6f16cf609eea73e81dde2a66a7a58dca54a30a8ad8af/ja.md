```julia
write_result_to_vtk(
    filename::String,
    data::PLaplace.PLaplaceData
) -> Union{Nothing, Vector{String}}

```

指定された名前のVTKファイルに結果ベクトルを書き込みます。ファイル自体は作成されますが、パスは事前に存在している必要があります。
