```julia
struct FileMesh{MeshObj} <: FiniteElementContainers.AbstractMesh
```

  * `file_name::String`
  * `mesh_obj::Any`

オープンメッシュファイルオブジェクトへのハンドルを持つメッシュタイプ。このタイプのメソッドは拡張で「オーバーライド」されます。

例としてFiniteElementContainersExodusExtを参照してください。
