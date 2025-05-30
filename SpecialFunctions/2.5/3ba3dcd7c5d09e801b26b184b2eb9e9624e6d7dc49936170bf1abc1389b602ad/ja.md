```
ellipe(m)
```

完全楕円積分の第2種 $E(m)$ をパラメータ $m$ に対して計算します。

$$
\operatorname{ellipe}(m)
= E(m)
= \int_0^{ \frac{\pi}{2} } \sqrt{1 - m \sin^2 \theta} \, \mathrm{d}\theta
\quad \text{for} \quad m \in \left( -\infty, 1 \right] .
$$

外部リンク: [DLMF 19.2.8](https://dlmf.nist.gov/19.2.8), [Wikipedia](https://en.wikipedia.org/wiki/Elliptic_integral#Complete_elliptic_integral_of_the_second_kind).

参照: [`ellipk(m)`](@ref SpecialFunctions.ellipk).

# 引数

  * `m`: パラメータ $m$ は、領域 $(-\infty,1]$ に制限され、楕円モジュラス $k$ に $k^2=m$ で関連し、モジュラー角 $\alpha$ に $k=\sin \alpha$ で関連します。

# 実装

[fukushima_2015](@citet) に示されているように、区分的近似多項式を使用します。

$$
m<0
$$

の場合は、[fukushima_2015](@citet) に従います。

この論文で提案されているように、領域は $(-\infty,1]$ に制限されています。
