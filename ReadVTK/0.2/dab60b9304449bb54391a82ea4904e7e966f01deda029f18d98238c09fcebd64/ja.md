```
VTKPrimitives{接続性, オフセット}
```

VTK PolyDataファイルから`connectivity`と`offsets`情報を一次元配列のようなコンテナとして保存します。`connectivity`と`offset`配列を実際の幾何学的ポイントに接続する方法については、[VTKファイル形式のドキュメント](http://vtk.org/VTK/img/file-formats.pdf)を参照してください。

`VTKPrimitives`オブジェクトからセルの数を決定するために`length`を使用できます。
