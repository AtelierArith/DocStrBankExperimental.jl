```julia
construct_interpolations(x, y; method, order, extrapolation)

```

ネストされた配列の補間を構築します。`x` が `AbstractRange` の場合、ネストされた配列は補間のために多次元配列に変換されます。それ以外の場合は、「グリッド化」メソッドと `order` 1 のみがサポートされています。
