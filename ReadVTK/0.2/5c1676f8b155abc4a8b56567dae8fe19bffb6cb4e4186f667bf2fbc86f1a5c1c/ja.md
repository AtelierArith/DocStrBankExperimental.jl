```
to_meshcells(cells::VTKCells)
```

`VTKCells`オブジェクトを変換します。これは、複数のセルの生のポイントおよび接続データを保持します。これを`MeshCell`オブジェクトのベクターに変換します。後者は、例えば、新しいVTKファイルを書き込むためにWriteVTK.jlパッケージに渡すことができます。詳細については、[`VTKCells`](@ref)、[`VTKBase.MeshCell`](@ref)を参照してください。
