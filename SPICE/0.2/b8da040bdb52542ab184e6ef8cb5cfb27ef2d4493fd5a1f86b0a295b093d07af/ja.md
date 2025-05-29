```
dafec(handle; bufsiz=256, lenout=1024)
```

バイナリ DAF のコメントエリアからコメントを抽出します。

### 引数

  * `handle`: 読み取りアクセスで開かれたバイナリ DAF のハンドル
  * `bufsiz`: バッファの最大サイズ（行数）（デフォルト: 256）
  * `lenout`: 出力バッファ内の文字列の長さ（デフォルト: 1024）

### 出力

抽出されたコメント行が配置されるバッファを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dafec_c.html)
