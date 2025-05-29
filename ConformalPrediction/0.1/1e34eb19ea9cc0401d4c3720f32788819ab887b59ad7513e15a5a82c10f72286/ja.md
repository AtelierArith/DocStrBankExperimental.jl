```
MMI.fit(conf_model::SimpleInductiveRegressor, verbosity, X, y)
```

[`SimpleInductiveRegressor`](@ref) の非適合スコアは次のように計算されます：

$$
S_i^{\text{CAL}} = s(X_i, Y_i) = h(\hat\mu(X_i), Y_i), \ i \in \mathcal{D}_{\text{calibration}}
$$

ヒューリスティック関数の典型的な選択は $h(\hat\mu(X_i),Y_i)=|Y_i-\hat\mu(X_i)|$ であり、ここで $\hat\mu$ はトレーニングデータ $\mathcal{D}_{\text{train}}$ にフィットしたモデルを示します。
