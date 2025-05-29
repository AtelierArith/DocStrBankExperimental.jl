```
molteno_dim(X::AbstractStateSpaceSet; k0::Int = 10, q = 1.0, base = 2)
```

`X`の[`generalized_dim`](@ref)の推定値を[Molteno1993](@cite)によるアルゴリズムを使用して返します。この関数は[`molteno_boxing`](@ref)によって推定された確率の単純な利用ですので、詳細についてはその関数を参照してください。ここでは、各サイズで確率のエントロピーが計算され、エントロピー対ログ(サイズ)のグラフに直線がフィットされます。これは[`generalized_dim`](@ref)と同様です。
