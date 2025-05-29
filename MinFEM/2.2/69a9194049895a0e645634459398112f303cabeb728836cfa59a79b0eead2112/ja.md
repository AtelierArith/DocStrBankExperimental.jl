```julia
open_vtkfile_boundary(
    mesh::MinFEM.Mesh,
    file_name::String,
    boundaryElements::Set{Int64}
) -> WriteVTK.DatasetFile

```

新しいVTK出力ファイルを開き、メッシュデータを書き込みます。
