```
ekucei(handle, segno, recno, column, dvals, isnull)
```

指定されたEKレコードの整数列エントリを更新します。

### 引数

  * `handle`: EKファイルに接続されたハンドル
  * `segno`: レコードを含むセグメントのインデックス
  * `recno`: エントリを更新するレコード
  * `column`: 列名
  * `ivals`: 新しい列エントリを構成する整数値
  * `isnull`: 列エントリがnullであるかどうかを示すフラグ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekucei_c.html)
