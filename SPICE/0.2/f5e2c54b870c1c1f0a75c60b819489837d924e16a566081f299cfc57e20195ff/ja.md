```
ekrcec(handle, segno, recno, column, lenout=256, nelts=100)
```

指定されたEKレコードから文字列列のデータを読み取ります。

### 引数

  * `handle`: EKファイルに接続されたハンドル
  * `segno`: レコードを含むセグメントのインデックス
  * `recno`: データを読み取るレコード
  * `column`: 列名
  * `lenout`: 出力文字列の最大長
  * `nelts`: 戻り値の最大要素数（デフォルト: 100）

### 出力

列エントリの文字値を返すか、nullの場合は`missing`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekrcec_c.html)
