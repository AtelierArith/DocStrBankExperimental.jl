```
InverseGamma(α, θ)
```

*逆ガンマ分布*は、形状パラメータ`α`とスケール`θ`を持ち、確率密度関数は次のようになります。

$$
f(x; \alpha, \theta) = \frac{\theta^\alpha x^{-(\alpha + 1)}}{\Gamma(\alpha)}
e^{-\frac{\theta}{x}}, \quad x > 0
$$

これは[`ガンマ`](@ref)分布に関連しています：もし$X \sim \operatorname{Gamma}(\alpha, \beta)$であれば、$1 / X \sim \operatorname{InverseGamma}(\alpha, \beta^{-1})$です。

```julia
InverseGamma()        # 単位形状と単位スケールの逆ガンマ分布、すなわちInverseGamma(1, 1)
InverseGamma(α)       # 形状αと単位スケールの逆ガンマ分布、すなわちInverseGamma(α, 1)
InverseGamma(α, θ)    # 形状αとスケールθの逆ガンマ分布

params(d)        # パラメータを取得、すなわち(α, θ)
shape(d)         # 形状パラメータを取得、すなわちα
scale(d)         # スケールパラメータを取得、すなわちθ
```

外部リンク

  * [逆ガンマ分布 - Wikipedia](http://en.wikipedia.org/wiki/Inverse-gamma_distribution)
