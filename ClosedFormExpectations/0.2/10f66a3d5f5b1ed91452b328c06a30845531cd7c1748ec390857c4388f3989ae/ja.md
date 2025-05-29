```
LinearLogGamma(α, β, weights)
```

LogGamma分布から導出された非正規化多変量分布です。（LogGammaを参照）

LinearLogGamma分布は、LogGamma分布から導出された多次元`x`上の分布です。次のように定義されます：

$$
    LLG(x | lpha, eta, w) = LG(x^T w | a, b),
$$

ここで、weightsは固定された共変量のベクトルであり、lphaとetaはそれぞれLogGamma分布のスケールパラメータと形状パラメータです。フィールド

α::T: LogGamma分布のスケールパラメータ。

β::T: LogGamma分布の形状パラメータ。

weights::C: 固定された共変量のベクトル。
