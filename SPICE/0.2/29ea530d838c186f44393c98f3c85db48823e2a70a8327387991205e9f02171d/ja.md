```
ekuced(handle, segno, recno, column, dvals, isnull)
```

指定されたEKレコードの倍精度列エントリを更新します。

### 引数

  * `handle`: EKファイルに接続されたハンドル
  * `segno`: レコードを含むセグメントのインデックス
  * `recno`: エントリを更新するレコード
  * `column`: 列名
  * `dvals`: 新しい列エントリを構成する倍精度値
  * `isnull`: 列エントリがnullであるかどうかを示すフラグ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekuced_c.html)
