```
aic(fm:::MaximumLikelihoodAbstractExtremeValueModel)
```

最大尤度法によってフィッティングされたモデルの赤池情報量基準（AIC）を計算します。

## 詳細

AICは次のように定義されます：

$$
AIC = 2 k - 2 \log \hat{L};
$$

ここで、$k$は推定されたパラメータの数であり、$\hat{L}$はモデルの尤度関数の最大化された値です。
