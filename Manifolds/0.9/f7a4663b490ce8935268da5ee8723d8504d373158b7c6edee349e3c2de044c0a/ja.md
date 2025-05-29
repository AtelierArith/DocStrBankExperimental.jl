```
exp(M::EssentialManifold, p, X)
```

[`EssentialManifold`](@ref)上の点`p`から方向`X`への指数写像を計算します。すなわち、

$$
\text{exp}_p(X) =\text{exp}_g( \tilde X),  \quad g \in \text(SO)(3)^2,
$$

ここで、$\tilde X$は$X$の水平リフトです[TronDaniilidis:2017](@cite)。
