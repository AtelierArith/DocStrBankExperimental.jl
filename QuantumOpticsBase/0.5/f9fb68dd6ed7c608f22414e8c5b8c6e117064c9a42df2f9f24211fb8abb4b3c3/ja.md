```
LazySum([Tf,] [factors,] operators)
LazySum([Tf,] basis_l, basis_r, [factors,] [operators])
LazySum(::Tuple, x::LazySum)
```

演算子の和の遅延評価。

すべての演算子は同じ基底に関して与えられる必要があります。フィールド `factors` は、`operators` フィールドに格納されている各演算子に対する追加の乗法因子を考慮します。

因子型 `Tf` は、因子や演算子自体から推測する必要がないように指定できます。すべての `factors` は型 `Tf` に変換されます。

`operators` はそのまま保持されます。例えば、演算子の `Tuple` や `Vector` である可能性があります。演算子状態操作の実行時パフォーマンスを向上させるために、`Tuple` の使用が推奨されます。`Vector` は、`LazySum` の合計など、`LazySum` に対する算術を行う際にコンパイル時のオーバーヘッドを減少させることができます。

ベクターベースの `LazySum` `x` を演算子ストレージにタプルを使用するように変換するには、`LazySum(::Tuple, x)` を使用します。
