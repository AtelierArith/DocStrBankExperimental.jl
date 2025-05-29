```
dasrfr(handle, idwlen=128, ifnlen=256)
```

DASのファイルレコードの内容を読み取ります。

### 引数

  * `handle`: DASファイルハンドル
  * `idwlen`: IDワード文字列の長さ（デフォルト: 128）
  * `ifnlen`: 内部ファイル名文字列の長さ（デフォルト: 256）

### 出力

  * `idword`: IDワード
  * `ifname`: DAS内部ファイル名
  * `nresvr`: ファイル内の予約レコードの数
  * `nresvc`: 予約レコード領域で使用中の文字数
  * `ncomr`: ファイル内のコメントレコードの数
  * `ncomc`: コメント領域で使用中の文字数

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dasrfr_c.html)
