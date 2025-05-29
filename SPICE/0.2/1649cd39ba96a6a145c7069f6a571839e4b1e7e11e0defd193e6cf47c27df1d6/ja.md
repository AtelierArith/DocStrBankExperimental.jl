```
kdata(which, kind, fillen=1024, srclen=256)
```

指定されたカーネルタイプのリストの中から n 番目のカーネルのデータを返します。

### 引数

  * `which`: カーネルのリストから取得するカーネルのインデックス
  * `kind`: 取得が制限されるカーネルの種類
  * `fillen`: 出力ファイル文字列の利用可能なスペース
  * `srclen`: 出力ソース文字列の利用可能なスペース

### 出力

カーネルが見つからなかった場合は `nothing` を返し、見つかった場合は次の要素からなるタプルを返します。

  * `file`: カーネルファイルの名前
  * `filtyp`: カーネルのタイプ
  * `source`: ファイルをロードするために使用されたソースファイルの名前
  * `handle`: ファイルに添付されたハンドル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/kdata_c.html)
