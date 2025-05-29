```
MMI.fit(conf_model::ConformalQuantileRegressor, verbosity, X, y)
```

[`ConformalQuantileRegressor`](@ref) の非適合性スコアは次のように計算されます：

$$
S_i^{\text{CAL}} = s(X_i, Y_i) = h(\hat\mu_{\alpha_{lo}}(X_i), \hat\mu_{\alpha_{hi}}(X_i)  ,Y_i), \ i \in \mathcal{D}_{\text{calibration}}
$$

ヒューリスティック関数の典型的な選択は $h(\hat\mu_{\alpha_{lo}}(X_i), \hat\mu_{\alpha_{hi}}(X_i)  ,Y_i)= max\{\hat\mu_{\alpha_{low}}(X_i)-Y_i, Y_i-\hat\mu_{\alpha_{hi}}(X_i)\}$ であり、ここで $\hat\mu$ はトレーニングデータ $\mathcal{D}_{\text{train}}` にフィットしたモデルを示し、$\alpha*{lo}, \alpha*{hi}`` はそれぞれ下位および上位パーセンタイルを示します。
