```
ekucec(handle, segno, recno, column, cvals, isnull)
```

指定されたEKレコードの文字列列エントリを更新します。

### 引数

  * `handle`: EKファイルハンドル
  * `segno`: レコードを含むセグメントのインデックス
  * `recno`: データを更新するレコード
  * `column`: 列名
  * `cvals`: 新しい列エントリを構成する文字列値
  * `isnull`: 列エントリがnullであるかどうかを示すフラグ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekucec_c.html)
