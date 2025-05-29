```
MMI.fit(conf_model::JackknifeRegressor, verbosity, X, y)
```

[`JackknifeRegressor`](@ref) の非適合スコアは、次のようにして一つを除く（LOO）手法を通じて計算されます。

$$
S_i^{\text{LOO}} = s(X_i, Y_i) = h(\hat\mu_{-i}(X_i), Y_i), \ i \in \mathcal{D}_{\text{train}}
$$

ここで、$\hat\mu_{-i}(X_i)$ は $X_i$ に対する一つを除く予測を示します。言い換えれば、各トレーニングインスタンス $i=1,...,n$ に対して、モデルは $i$ を除くすべてのトレーニングデータで訓練されます。フィッティングされたモデルは、その後 $X_i$ からのサンプル外予測に使用されます。対応する非適合スコアは、フィッティングされた値 $\hat\mu_{-i}(X_i)$ と真の値 $Y_i$ にヒューリスティックな不確実性測定 $h(\cdot)$ を適用することによって計算されます。
