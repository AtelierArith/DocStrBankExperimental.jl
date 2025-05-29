```
MMI.fit(conf_model::NaiveRegressor, verbosity, X, y)
```

[`NaiveRegressor`](@ref) の非適合スコアは、次のようにサンプル内で計算されます：

$$
S_i^{\text{IS}} = s(X_i, Y_i) = h(\hat\mu(X_i), Y_i), \ i \in \mathcal{D}_{\text{train}}
$$

ヒューリスティック関数の一般的な選択は $h(\hat\mu(X_i),Y_i)=|Y_i-\hat\mu(X_i)|$ であり、ここで $\hat\mu$ はトレーニングデータ $\mathcal{D}_{\text{train}}$ にフィットしたモデルを示します。
