```
fits_get_coltype(f::FITSFile, colnum::Integer)
```

現在のHDUがASCIIまたはバイナリテーブルのいずれかを含む場合、位置`colnum`（1から数える）にある列に関する情報を返します。

返り値はタプルで、以下を含みます。

  * `typecode`: 列のCFITSIO整数型コード。
  * `repcount`: 列の繰り返しカウント。
  * `width`: 個々の要素の幅。
