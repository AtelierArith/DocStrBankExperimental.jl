```
ekrced(handle, segno, recno, column, nelts=100)
```

指定されたEKレコードから倍精度列のデータを読み取ります。

### 引数

  * `handle`: EKファイルに接続されたハンドル
  * `segno`: レコードを含むセグメントのインデックス
  * `recno`: データを読み取るレコード
  * `column`: 列名
  * `nelts`: 返す最大要素数（デフォルト: 100）

### 出力

列エントリの値を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekrced_c.html)
