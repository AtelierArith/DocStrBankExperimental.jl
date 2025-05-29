```
MMI.predict(conf_model::CVMinMaxRegressor, fitresult, Xnew)
```

For the [`CVMinMaxRegressor`](@ref) 予測区間は次のように計算されます。

$$
\hat{C}_{n,\alpha}(X_{n+1}) = \left[ \min_{i=1,...,n} \hat\mu_{-\mathcal{D}_{k(i)}}(X_{n+1}) -  \hat{q}_{n, \alpha}^{+} \{S_i^{\text{CV}} \}, \max_{i=1,...,n} \hat\mu_{-\mathcal{D}_{k(i)}}(X_{n+1}) + \hat{q}_{n, \alpha}^{+} \{ S_i^{\text{CV}}\} \right] , i \in \mathcal{D}_{\text{train}}
$$

ここで、$\hat\mu_{-\mathcal{D}_{k(i)}}$ は、$i$ 番目の点が除外されたサブセット $\mathcal{D}_{k(i)}$ を持つトレーニングデータにフィットしたモデルを示します。
