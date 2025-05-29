```
srfs2c(srfstr, bodstr)
```

サーフェス文字列とボディ文字列を対応するサーフェスIDコードに変換します。入力文字列には名前または整数IDコードが含まれている場合があります。

### 引数

  * `srfstr`: サーフェス名またはID文字列
  * `bodstr`: ボディ名またはID文字列

### 出力

見つかった場合はサーフェスIDコードを返し、そうでない場合は`nothing`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/srfs2c_c.html)
