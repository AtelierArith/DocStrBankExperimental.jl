```
FindConfBoundary(DM::AbstractDataModel, Confnum::Real; BoolTest::Bool=(Confnum > 8), Ftest::Bool=false, tol::Real=4e-15)
```

信頼区間のレベル `Confnum`σ の境界にあるパラメータ構成を見つけます。

  * `BoolTest` は、閾値が `Bool` 値のテストまたは `Float` 値のテストを使用して見つけられるかどうかを指定するために使用できます。メモリを少なく使用するため、`Bool` 値のテストは `BigFloat` を使用する場合（すなわち、Confnum > 8 の場合）にパフォーマンスが向上します。
  * `Ftest=true` は、閾値を定義するためにウィルクス検定の代わりにF検定を使用します。通常、F検定は小さなサンプルサイズを考慮するため、より保守的な推定（すなわち、より大きな信頼区間）をもたらします。
