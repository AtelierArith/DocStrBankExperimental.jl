```
VTKCells{Connectivity, Offsets, Types}
```

VTKファイルから`connectivity`、`offsets`、および`types`情報を一次元配列のようなコンテナとして保存します。`connectivity`および`offset`配列を実際の幾何学的ポイントに接続する方法については、[VTKファイル形式のドキュメント](http://vtk.org/VTK/img/file-formats.pdf)を参照してください。

`VTKCells`オブジェクトからセルの数を決定するには、`length`を使用できます。

参照: [`get_points`](@ref)
