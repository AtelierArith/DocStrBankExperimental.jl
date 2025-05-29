```
AsymmetricRelativeEntropy <: ProbabilityDensityDM
```

確率密度および時間周波数に基づくエネルギーマップのための非対称相対エントロピー識別測度。この測度は交差エントロピーおよびクルバック・ライブラー発散としても知られています。

方程式:

$$
D(p,q) = \sum p(x) \log \frac{p(x)}{q(x)}
$$

ここで、$\int_{-\infty}^{\infty} p(t) dt = \int_{-\infty}^{\infty} q(t) dt = 1$ （$p(t)$ および $q(t)$ は確率密度関数です。）
