```
ekifld(handle, tabnam, nrows, cnames, decls)
```

新しいEカーネルセグメントを初期化して、高速書き込みを可能にします。

### 引数

  * `handle`: ファイルハンドル
  * `tabnam`: テーブル名
  * `nrows`: セグメント内の行数
  * `cnames`: 列の名前
  * `decls`: 列の宣言

### 出力

  * `segno`: セグメント番号
  * `rcptrs`: レコードポインタの配列

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekifld_c.html)
