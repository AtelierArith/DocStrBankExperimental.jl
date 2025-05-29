```
ekgd(selidx, row, element)
```

指定された行の列のダブル精度型のエントリの要素を返します。

### 引数

  * `selidx`: SELECT句内の親列のインデックス
  * `row`: 取得する行
  * `element`: 取得する列エントリ内の要素のインデックス

### 出力

列エントリのダブル精度要素を返すか、nullの場合は`missing`、列が見つからなかった場合は`nothing`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekgd_c.html)
