```
MMI.predict(conf_model::CVPlusRegressor, fitresult, Xnew)
```

[`CVPlusRegressor`](@ref) の予測区間は、[`JackknifePlusRegressor`](@ref) とほぼ同じ方法で計算されます。具体的には、次のようになります。

$$
\hat{C}_{n,\alpha}(X_{n+1}) = \left[ \hat{q}_{n, \alpha}^{-} \{\hat\mu_{-\mathcal{D}_{k(i)}}(X_{n+1}) - S_i^{\text{CV}} \}, \hat{q}_{n, \alpha}^{+} \{\hat\mu_{-\mathcal{D}_{k(i)}}(X_{n+1}) + S_i^{\text{CV}}\} \right] , \ i \in \mathcal{D}_{\text{train}}
$$

ここで、$\hat\mu_{-\mathcal{D}_{k(i)}}$ は、$i$ 番目の点が除外されたフォールド $\mathcal{D}_{k(i)}$ を持つトレーニングデータにフィットしたモデルを示します。

[`JackknifePlusRegressor`](@ref) は、$K=n$ の場合の [`CVPlusRegressor`](@ref) の特別なケースです。
