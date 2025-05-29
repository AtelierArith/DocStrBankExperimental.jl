```
open_vtkfile_boundary(
    mesh::Mesh,
    file_name::String;
    boundary = Set{Boundary}()
)
```

新しいVTK出力ファイルを開き、メッシュデータを書き込みます。
