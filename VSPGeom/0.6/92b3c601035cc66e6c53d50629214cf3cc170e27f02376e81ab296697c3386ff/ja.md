```
readDegenGeom(filename::String; verbose::Bool=false)
```

OpenVSPによって出力されたDegenGeom CSVファイルを読み込み、ジオメトリとコンポーネントを取得します。

**引数**

  * `filename::String`: DegenGeomファイル名
  * `verbose::Bool`: ファイル読み取り操作中にステータスメッセージを表示するには`true`に設定します

**戻り値**

  * `comp`: [`VSPComponent`](@ref)オブジェクトのベクター

```
