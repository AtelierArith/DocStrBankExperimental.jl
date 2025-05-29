```
bic(fm:::MaximumLikelihoodAbstractExtremeValueModel)
```

最大尤度法によってフィッティングされたモデルのベイズ情報基準（BIC）を計算します。

## 詳細

BICは次のように定義されます：

$$
BIC = k \log n - 2 \log \hat{L};
$$

ここで、$k$は推定されたパラメータの数、$n$はデータの数、$\hat{L}$はモデルのための尤度関数の最大化された値です。
