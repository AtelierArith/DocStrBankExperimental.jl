```
MMI.fit(conf_model::CVPlusRegressor, verbosity, X, y)
```

[`CVPlusRegressor`](@ref) の非適合スコアは、次のように交差検証 (CV) を通じて計算されます。

$$
S_i^{\text{CV}} = s(X_i, Y_i) = h(\hat\mu_{-\mathcal{D}_{k(i)}}(X_i), Y_i), \ i \in \mathcal{D}_{\text{train}}
$$

ここで、$\hat\mu_{-\mathcal{D}_{k(i)}}(X_i)$ は $X_i$ に対する CV 予測を示します。言い換えれば、各 CV フォールド $k=1,...,K$ と各トレーニングインスタンス $i=1,...,n$ に対して、モデルは $i$ を含むフォールドを除くすべてのトレーニングデータでトレーニングされます。フィッティングされたモデルは、その後 $X_i$ からのサンプル外予測に使用されます。対応する非適合スコアは、フィッティングされた値 $\hat\mu_{-\mathcal{D}_{k(i)}}(X_i)$ と真の値 $Y_i$ にヒューリスティックな不確実性測定 $h(\cdot)$ を適用することによって計算されます。
