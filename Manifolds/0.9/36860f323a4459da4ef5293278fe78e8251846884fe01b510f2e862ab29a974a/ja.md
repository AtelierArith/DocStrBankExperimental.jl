```
exp(G::GeneralLinear, p, X)
```

[`GeneralLinear`](@ref)群の指数写像を計算します。

指数写像は次のようになります。

$$
\exp_p \colon X ↦ p \operatorname{Exp}(X^\mathrm{H}) \operatorname{Exp}(X - X^\mathrm{H}),
$$

ここで、$\operatorname{Exp}(⋅)$は行列の指数を示し、$⋅^\mathrm{H}$は共役転置を示します [AndruchowLarotondaRechtVarela:2014](@cite) [MartinNeff:2016](@cite)。
