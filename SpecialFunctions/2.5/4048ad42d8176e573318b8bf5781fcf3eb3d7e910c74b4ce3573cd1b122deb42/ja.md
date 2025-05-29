```
ellipk(m)
```

完全楕円積分の第1種 $K(m)$ をパラメータ $m$ に対して計算します。

$$
\operatorname{ellipk}(m)
= K(m)
= \int_0^{ \frac{\pi}{2} } \frac{1}{\sqrt{1 - m \sin^2 \theta}} \, \mathrm{d}\theta
\quad \text{for} \quad m \in \left( -\infty, 1 \right] \, .
$$

外部リンク: [DLMF 19.2.8](https://dlmf.nist.gov/19.2.8), [Wikipedia](https://en.wikipedia.org/wiki/Elliptic_integral#Notational_variants).

関連項目: [`ellipe(m)`](@ref SpecialFunctions.ellipe).

# 引数

  * `m`: パラメータ $m$ は、領域 $(-\infty,1]$ に制限され、楕円モジュラス $k$ に $k^2=m$ で関連し、モジュラー角 $\alpha$ に $k = \sin \alpha$ で関連します。

# 実装

以下に示すように、区分近似多項式を使用します。

> 'Fast Computation of Complete Elliptic Integrals and Jacobian Elliptic Functions', Fukushima, Toshio. (2014). F09-FastEI. Celest Mech Dyn Astr, DOI 10.1007/s10569-009-9228-z, [https://pdfs.semanticscholar.org/8112/c1f56e833476b61fc54d41e194c962fbe647.pdf](https://pdfs.semanticscholar.org/8112/c1f56e833476b61fc54d41e194c962fbe647.pdf)


$$
m<0
$$

の場合は、次のように続きます。

> Fukushima, Toshio. (2014). 'Precise, compact, and fast computation of complete elliptic integrals by piecewise minimax rational function approximation'. Journal of Computational and Applied Mathematics. 282. DOI 10.13140/2.1.1946.6245., [https://www.researchgate.net/publication/267330394](https://www.researchgate.net/publication/267330394)


この論文で提案されているように、領域は $(-\infty,1]$ に制限されています。
