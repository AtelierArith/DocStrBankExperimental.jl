```
get_unused_symbols(model::Model; filter_known_unused=false)
```

使用されていない変数、ショック、およびパラメータのベクトルを含む辞書を返します。

キーワード引数:

  * filter*known*unused::Bool - `true` の場合、結果には model.option.unused_varshks に存在する変数は含まれません。デフォルトは `false` です。
