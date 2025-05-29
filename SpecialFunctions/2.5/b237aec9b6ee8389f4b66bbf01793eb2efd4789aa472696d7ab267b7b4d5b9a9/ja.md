```
expintx(z)
expintx(ν, z)
```

スケーリングされた指数関数積分を計算します

$$
\exp(z) \operatorname{E}_\nu(z) = e^z \int_1^\infty \frac{e^{-zt}}{t^\nu} \mathrm{d}t.
$$

もし$\nu$が指定されていない場合、$\nu = 1$が使用されます。任意の複素数$\nu$と$z$がサポートされています。

参照: [`expint(ν, z)`](@ref SpecialFunctions.expint)
