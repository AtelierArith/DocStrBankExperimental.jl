```
srfcss(code, bodstr)
```

表面IDコードを、ボディ文字列と共に対応する表面名に変換します。該当する表面名が存在しない場合は、表面IDコードの文字列表現を返します。

### 引数

  * `code`: 文字列に変換する整数の表面IDコード
  * `bodstr`: 表面に関連付けられたボディの名前またはID

### 出力

  * `srfstr`: 表面IDコードに対応する文字列
  * `isname`: 出力が表面名であることを示す論理フラグ

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/srfcss_c.html)
