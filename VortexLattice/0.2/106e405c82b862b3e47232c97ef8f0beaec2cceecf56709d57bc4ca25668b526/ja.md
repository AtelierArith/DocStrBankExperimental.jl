```
`read_degengeom(filename::String)`
```

OpenVSPによって書き出されたDegenGeomファイルからすべてのジオメトリコンポーネントを読み取ります。

**引数**

  * `filename::String`: DegenGeomファイル名

**戻り値**

  * `comp`: `vsp.VSPComponent`オブジェクトのベクター
