```
loglikelihood(arnet::ArNet, arvar::ArVar)
```

モデル `arnet` の下で `arvar.Z` から計算された対数尤度のベクトルを返します。`size(arvar.Z) == N,M` であり、ここで `N` はシーケンスの長さ、`M` はシーケンスの数です。返されるベクトルは `arvar.W` によって再重み付けされた `M` 要素を持ちます。
