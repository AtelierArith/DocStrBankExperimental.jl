```
estimate_boxsizes(X::AbstractStateSpaceSet; kwargs...) → εs
```

`k` 個の指数間隔の値を返します: `εs = base .^ range(lower + w, upper + z; length = k)`、これはフラクタル次元を計算する際に使用されるサイズ ε の良い推定値です。この関数を使用する前に、入力データセットを [`standardize`](@ref) することを強く推奨します。

`d₋` を `X` における最小のペアワイズ距離とし、`d₋ = dminimum_pairwise_distance(X)` とします。`d₊` を `X` の平均総長とし、`d₊ = mean(ma - mi)` で、`mi, ma = minmaxima(X)` です。したがって、`lower = log(base, d₋)` および `upper = log(base, d₊)` となります。デフォルトでは `w=1, z=-1` であるため、返されるサイズは最小距離よりも1桁大きく、最大距離よりも1桁小さくなります。

## キーワード

  * `w = 1, z = -1, k = 16` : 上記のように説明されています。
  * `base = MathConstants.e` : `log` 関数で使用される基数。
  * `warning = true`: 悪い推定値に対していくつかの警告を表示します。
  * `autoexpand = true`: 最終的な推定範囲が少なくとも2桁のオーダーをカバーしていない場合、`w -= we` および `z -= ze` を設定することで自動的に拡張されます。キーワード `we = w, ze = z` に異なるデフォルト値を設定できます。
