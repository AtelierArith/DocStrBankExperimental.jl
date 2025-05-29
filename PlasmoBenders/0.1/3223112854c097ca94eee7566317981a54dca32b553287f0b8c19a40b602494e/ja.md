```
get_upper_bounds(optimizer::BendersAlgorithm; monotonic = true)
```

`BendersAlgorithm`オブジェクトから`upper_bounds`の値を返します。これは各イテレーションでの上限のベクトルです。各イテレーションで返される上限は、単調に減少することが保証されていません。`monotonic=true`の場合、この関数は各イテレーションまでに見た最良の上限を返します（そのイテレーションで見た実行可能な解の値ではなく）。
