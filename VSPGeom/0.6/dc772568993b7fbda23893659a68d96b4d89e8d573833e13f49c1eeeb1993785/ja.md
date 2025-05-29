```
readSTL(filename::String; verbose::Bool=false, tol::Float64=eps(Float64), zeroBased::Bool=false)
```

STLファイルを読み込んでジオメトリを取得します。この関数は、OpenVSPが出力する非標準のTagged Multi Solidファイルタイプも処理できます。メッシュの接続情報は現在利用できません。

**引数**

  * `filename::String`: STLファイル名
  * `verbose::Bool`: ファイル読み込み操作中にステータスメッセージを表示するには`true`に設定します
  * `tol::Float64`: 接続を取得するためにポイントを比較する際の絶対許容誤差を設定します
  * `zeroBased::Bool`: 接続情報のインデックスに[ゼロベースの番号付け](https://en.wikipedia.org/wiki/Zero-based_numbering)を使用するには`true`に設定します

**戻り値**

  * `geom`: ['Geometrybasics.jl'](https://juliageometry.github.io/GeometryBasics.jl/stable/)パッケージからの`GeometryBasics.Mesh`オブジェクトのベクター
