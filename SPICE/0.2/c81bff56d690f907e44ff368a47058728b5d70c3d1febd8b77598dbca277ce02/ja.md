```
ekacec(handle, segno, recno, column, cvals, isnull)
```

指定されたEKレコードに文字列列のデータを追加します。

### 引数

  * `handle`: EKファイルハンドル
  * `segno`: レコードを含むセグメントのインデックス
  * `recno`: データを追加するレコード
  * `column`: 列名
  * `cvals`: 列に追加する文字列値
  * `isnull`: 列エントリがnullであるかどうかを示すフラグ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekacec_c.html)
