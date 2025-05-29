```
kinfo(file, srclen=256)
```

### 引数

  * `file`: 情報を取得するカーネルの名前
  * `srclen`: 出力ソース文字列の利用可能なスペース

### 出力

カーネルが見つからなかった場合は `nothing` を返し、見つかった場合は次の要素からなるタプルを返します。

  * `filtyp`: カーネルのタイプ
  * `source`: ファイルをロードするために使用されたソースファイルの名前
  * `handle`: ファイルに付随するハンドル

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/kinfo_c.html)
