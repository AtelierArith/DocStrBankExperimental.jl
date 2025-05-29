```
ekcii(table, cindex, lenout=256)
```

読み込まれたEKテーブルに属する列の属性情報を返します。列はテーブルとインデックスで指定します。

### 引数

  * `table`: 列を含むテーブルの名前
  * `cindex`: 属性を見つける列のインデックス
  * `lenout`: 列名の最大許容長（デフォルト: 256）

### 出力

  * `column`: 列の名前
  * `attdsc`: 列属性記述子

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekcii_c.html)
