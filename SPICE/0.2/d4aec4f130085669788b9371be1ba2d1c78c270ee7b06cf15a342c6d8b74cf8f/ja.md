```
ekgi(selidx, row, element)
```

指定された行の整数型の列のエントリから要素を返します。

### 引数

  * `selidx`: SELECT句における親列のインデックス
  * `row`: 取得する行
  * `elment`: 取得する列エントリ内の要素のインデックス

### 出力

列エントリの整数要素を返すか、nullの場合は`missing`、列が見つからなかった場合は`nothing`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekgi_c.html)
