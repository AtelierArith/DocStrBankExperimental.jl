```
srfc2s(code, bodyid)
```

表面IDコードとボディIDコードを翻訳して、対応する表面名を取得します。該当する名前が存在しない場合は、表面IDコードの文字列表現を返します。

### 引数

  * `code`: 文字列に翻訳する整数の表面IDコード
  * `bodyid`: 表面に関連するボディのIDコード

### 出力

  * `srfstr`: 表面IDコードに対応する文字列
  * `isname`: 出力が表面名であることを示す論理フラグ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/srfc2s_c.html)
