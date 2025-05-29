```
Strata(x::Symbol)
```

推定量を層別化するための式の構築において変数を保持する `StrataTerm` オブジェクトを作成します。

層別化の動作はフィッティングされた推定量に依存します：通常、[`StatsModels.jl`](https://github.com/JuliaStats/StatsModels.jl) の式の右側で次のように使用されます。

```
@formula(Surv(time,status) ~ Strata(covariate1) + covariate 2)
```

その後、ログランク型テストの層別化など、推定量に大きく依存する動作を持ちます。
