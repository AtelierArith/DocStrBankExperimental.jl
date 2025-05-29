```
MMI.fit(conf_model::SimpleInductiveClassifier, verbosity, X, y)
```

[`SimpleInductiveClassifier`](@ref) の非適合性スコアは次のように計算されます：

$$
S_i^{\text{CAL}} = s(X_i, Y_i) = h(\hat\mu(X_i), Y_i), \ i \in \mathcal{D}_{\text{calibration}}
$$

ヒューリスティック関数の典型的な選択は $h(\hat\mu(X_i), Y_i)=1-\hat\mu(X_i)_{Y_i}$ であり、ここで $\hat\mu(X_i)_{Y_i}$ は真のクラスのソフトマックス出力を示し、$\hat\mu$ はトレーニングデータ $\mathcal{D}_{\text{train}}$ にフィットしたモデルを示します。この単純なアプローチは、真のラベルのソフトマックス確率のみを考慮します。
