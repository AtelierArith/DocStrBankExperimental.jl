```
MMI.fit(conf_model::JackknifeMinMaxRegressor, verbosity, X, y)
```

[`JackknifeMinMaxRegressor`](@ref) の非適合スコアは、[`JackknifeRegressor`](@ref) と同様に計算されます。具体的には、次のようになります。

$$
S_i^{\text{LOO}} = s(X_i, Y_i) = h(\hat\mu_{-i}(X_i), Y_i), \ i \in \mathcal{D}_{\text{train}}
$$

ここで、$\hat\mu_{-i}(X_i)$ は $X_i$ に対する留一予測を示します。言い換えれば、各トレーニングインスタンス $i=1,...,n$ に対して、モデルは $i$ を除くすべてのトレーニングデータでトレーニングされます。フィッティングされたモデルは、その後 $X_i$ からのサンプル外予測に使用されます。対応する非適合スコアは、フィッティングされた値 $\hat\mu_{-i}(X_i)$ と真の値 $Y_i$ にヒューリスティックな不確実性測定 $h(\cdot)$ を適用することによって計算されます。
