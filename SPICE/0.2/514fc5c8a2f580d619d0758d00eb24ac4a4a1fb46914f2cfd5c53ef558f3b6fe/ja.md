```
srfscc(srfstr, bodyid)
```

サーフェス文字列を、ボディIDコードと共に、対応するサーフェスIDコードに変換します。入力サーフェス文字列には、名前または整数IDコードが含まれている場合があります。

### 引数

  * `srfstr`: サーフェス名またはID文字列
  * `bodyid`: ボディIDコード。

### 出力

見つかった場合はサーフェスIDコードを返し、そうでない場合は`nothing`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/srfscc_c.html)
