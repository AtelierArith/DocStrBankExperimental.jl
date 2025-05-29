```
ll = loglik(filter, u, y, p=parameters(filter))
ll = loglik(filter, u, y, x, p=parameters(filter))
```

全シーケンス `u,y` の対数尤度を計算します。

正確な状態シーケンス `x` が利用可能なカルマン型フィルタの場合、例えばシミュレーションや実験室設定からデータが得られる場合、出力予測誤差ではなく状態予測誤差を使用して対数尤度を計算できます。この場合、`logpdf(f.R, x-x̂)` が `logpdf(S, y-ŷ)` の代わりに使用されます。
