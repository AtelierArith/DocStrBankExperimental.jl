```
lx4num(string, first)
```

指定された開始位置から文字列をスキャンして、数値の終わりを探します。

### 引数

  * `string`: 任意の文字列
  * `first`: 文字列内でスキャンを開始する最初の文字

### 出力

  * `last`: 数値の一部である最後の文字。該当する文字がない場合、`last`は`first-1`の値で返されます。
  * `nchar`: 数値の文字数

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/lx4num_c.html)
