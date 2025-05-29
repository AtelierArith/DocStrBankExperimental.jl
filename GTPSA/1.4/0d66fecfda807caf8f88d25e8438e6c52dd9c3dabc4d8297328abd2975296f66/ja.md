```
@vars(descriptor [,complex=bool] [, dynamic=bool])
```

GTPSA `descriptor`内の各変数に対応する`TPS`のベクトルを構築します。

# キーワード引数

  * `complex` – `true`の場合、変数を`ComplexTPS64`として返します。デフォルトは`false`です。
  * `dynamic` – `true`の場合、変数は動的な`Descriptor`解決を使用します。デフォルトは`false`です。
