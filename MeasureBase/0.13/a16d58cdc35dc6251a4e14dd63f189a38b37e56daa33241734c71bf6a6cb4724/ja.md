```
likelihood_ratio(ℓ::Likelihood, p, q)
```

2つのパラメータの選択を比較するために、尤度比の対数を計算します。これは次のように等しいです。

```
density_rel(ℓ.k(p), ℓ.k(q), ℓ.x)
```

ただし、LogarithmicNumbers.jlを使用して計算され、アンダーフローやオーバーフローを回避します。`density_rel`は共通の基準測度を評価しない場合があるため、次のように計算するよりも効率的である可能性があります。

```
logdensityof(ℓ.k(p), ℓ.x) - logdensityof(ℓ.k(q), ℓ.x)
```
