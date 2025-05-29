```
logerfc(x)
```

自然対数の補完誤差関数の $x$ の値を計算します。すなわち、

$$
\operatorname{logerfc}(x) = \ln(\operatorname{erfc}(x))
\quad \text{for} \quad x \in \mathbb{R} \, .
$$

これは大きな $x$ に対する $\ln(\operatorname{erfc}(x))$ の正確なバージョンです。

外部リンク: [Wikipedia](https://en.wikipedia.org/wiki/Error_function).

参照: [`erfcx(x)`](@ref erfcx).

# 実装

[`erfc(x)`](@ref erfc) および [`erfcx(x)`](@ref erfcx) 関数に基づいています。
