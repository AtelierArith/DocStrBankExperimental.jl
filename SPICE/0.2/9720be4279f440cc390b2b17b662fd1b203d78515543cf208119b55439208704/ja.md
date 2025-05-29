```
ekgc(selidx, row, elment, lenout=256)
```

指定された行の文字型の列のエントリから要素を返します。

### 引数

  * `selidx`: SELECT句における親列のインデックス
  * `row`: 取得する行
  * `elment`: 取得する列エントリ内の要素のインデックス
  * `lenout`: 列要素の最大長（デフォルト: 256）

### 出力

列エントリの文字列要素を返すか、nullの場合は`missing`、列が見つからなかった場合は`nothing`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekgc_c.html)
