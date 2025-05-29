```
MMI.fit(conf_model::JackknifePlusMinMaxAbRegressor, verbosity, X, y)
```

[`JackknifePlusAbMinMaxRegressor`](@ref) の非適合スコアは次のようになります。

$$
S_i^{\text{J+MinMax}} = s(X_i, Y_i) = h(agg(\hat\mu_{B_{K(-i)}}(X_i)), Y_i), \ i \in \mathcal{D}_{\text{train}}
$$

ここで、$agg(\hat\mu_{B_{K(-i)}}(X_i))$ は、各 $X_i$ に対する集約予測（通常は平均または中央値）を示します（$K_{-i}$ は $X_i$ を含まないブートストラップです）。言い換えれば、Bモデルはブートストラップサンプリングで訓練され、フィッティングされたモデルは、サンプル外の $X_i$ の集約予測を作成するために使用されます。対応する非適合スコアは、フィッティングされた値 $agg(\hat\mu_{B_{K(-i)}}(X_i))$ と真の値 $Y_i$ にヒューリスティックな不確実性測定 $h(\cdot)$ を適用することによって計算されます。
