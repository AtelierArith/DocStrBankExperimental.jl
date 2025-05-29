```
@params(descriptor [,complex=bool] [, dynamic=bool])
```

GTPSA `descriptor`内の各パラメータに対応する`TPS`のベクトルを構築します。

# キーワード引数

  * `complex` – `true`の場合、パラメータを`ComplexTPS64`として返します。デフォルトは`false`です。
  * `dynamic` – `true`の場合、パラメータは動的な`Descriptor`解決を使用します。デフォルトは`false`です。
