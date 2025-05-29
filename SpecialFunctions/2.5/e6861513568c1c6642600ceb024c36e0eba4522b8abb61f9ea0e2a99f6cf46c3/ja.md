```
logerfcx(x)
```

自然対数のスケーリングされた補完誤差関数の $x$ の計算、すなわち

$$
\operatorname{logerfcx}(x) = \ln(\operatorname{erfcx}(x))
\quad \text{for} \quad x \in \mathbb{R} \, .
$$

これは大きくて負の $x$ に対する $\ln(\operatorname{erfcx}(x))$ の正確なバージョンです。

外部リンク: [Wikipedia](https://en.wikipedia.org/wiki/Error_function).

参照: [`erfcx(x)`](@ref erfcx).

# 実装

[`erfc(x)`](@ref erfc) および [`erfcx(x)`](@ref erfcx) 関数に基づいています。
