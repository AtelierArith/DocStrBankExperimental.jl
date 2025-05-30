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

以下のように、区分近似多項式を使用します。

> '完全楕円積分とヤコビ楕円関数の高速計算', 福島, 敏男. (2014). F09-FastEI. Celest Mech Dyn Astr, DOI 10.1007/s10569-009-9228-z, [https://pdfs.semanticscholar.org/8112/c1f56e833476b61fc54d41e194c962fbe647.pdf](https://pdfs.semanticscholar.org/8112/c1f56e833476b61fc54d41e194c962fbe647.pdf)


$$
m<0
$$

の場合は、次のように続きます。

> 福島, 敏男. (2014). '区分ミニマックス有理関数近似による完全楕円積分の正確でコンパクトかつ高速な計算'. Journal of Computational and Applied Mathematics. 282. DOI 10.13140/2.1.1946.6245., [https://www.researchgate.net/publication/267330394](https://www.researchgate.net/publication/267330394)


この論文で提案されているように、領域は $(-\infty,1]$ に制限されています。
