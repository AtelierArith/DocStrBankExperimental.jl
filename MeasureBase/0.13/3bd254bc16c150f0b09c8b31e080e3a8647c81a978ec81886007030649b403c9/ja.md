```
log_likelihood_ratio(ℓ::Likelihood, p, q)
```

二つのパラメータの選択を比較するために、尤度比の対数を計算します。これは次のように計算されます。

```
logdensity_rel(ℓ.k(p), ℓ.k(q), ℓ.x)
```

`logdensity_rel` は共通の基準測度を評価しない場合があるため、次の式よりも効率的である可能性があります。

```
logdensityof(ℓ.k(p), ℓ.x) - logdensityof(ℓ.k(q), ℓ.x)
```
