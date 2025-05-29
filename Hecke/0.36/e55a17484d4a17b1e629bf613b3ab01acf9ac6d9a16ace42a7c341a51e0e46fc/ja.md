```
pradical(O::AbsSimpleNumFieldOrder, p::{ZZRingElem|Integer}) -> AbsNumFieldOrderIdeal
```

与えられた素数 $p$ に対して、この関数は $\mathcal O$ の $p$-ラジカル $\sqrt{p\mathcal O}$ を返します。これは単に $\{ x \in \mathcal O \mid \exists k \in \mathbf Z_{\geq 0} \colon x^k \in p\mathcal O \}$ です。$p$ が素数であることは確認されません。
