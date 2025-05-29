```
exp(M::ProbabilitySimplex, p, X)
```

確率シンプレックス上の指数写像を計算します。

$$
\exp_pX = \frac{1}{2}\Bigl(p+\frac{X_p^2}{\lVert X_p \rVert^2}\Bigr)
+ \frac{1}{2}\Bigl(p - \frac{X_p^2}{\lVert X_p \rVert^2}\Bigr)\cos(\lVert X_p\rVert)
+ \frac{1}{\lVert X_p \rVert}\sqrt{p}\sin(\lVert X_p\rVert),
$$

ここで、$X_p = \frac{X}{\sqrt{p}}$であり、その除算は要素ごとに行われ、$X_p^2$および$\sqrt{p}$の演算も同様です。
