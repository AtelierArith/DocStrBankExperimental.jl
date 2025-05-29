```
MMI.fit(conf_model::NaiveClassifier, verbosity, X, y)
```

[`NaiveClassifier`](@ref) の非適合スコアは、次のようにサンプル内で計算されます：

$$
S_i^{\text{IS}} = s(X_i, Y_i) = h(\hat\mu(X_i), Y_i), \ i \in \mathcal{D}_{\text{calibration}}
$$

ヒューリスティック関数の一般的な選択は $h(\hat\mu(X_i), Y_i)=1-\hat\mu(X_i)_{Y_i}$ であり、ここで $\hat\mu(X_i)_{Y_i}$ は真のクラスのソフトマックス出力を示し、$\hat\mu$ はトレーニングデータ $\mathcal{D}_{\text{train}}$ にフィットしたモデルを示します。
