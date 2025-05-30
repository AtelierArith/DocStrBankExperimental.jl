```
SymmetricRelativeEntropy <: ProbabilityDensityDM
```

対称相対エントロピーは、確率密度と時間周波数エネルギーマップのための識別測度です。非対称相対エントロピーと似たアイデアですが、これは測度をより対称的にすることを目的としています。

式：非対称相対エントロピーを $D_A(p,q)$ と表すと、次のようになります。

$$
D(p,q) = D_A(p,q) + D_A(q,p) = \sum p(x) \log \frac{p(x)}{q(x)} + q(x) \log \frac{q(x)}{p(x)}
$$

ここで、$\int_{-\infty}^{\infty} p(t) dt = \int_{-\infty}^{\infty} q(t) dt = 1$ （$p(t)$ と $q(t)$ は確率密度関数です。）

**参照:** [`AsymmetricRelativeEntropy`](@ref)
