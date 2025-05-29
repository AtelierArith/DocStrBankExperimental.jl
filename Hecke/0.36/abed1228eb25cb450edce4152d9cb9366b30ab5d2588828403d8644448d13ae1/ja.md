```
  pradical(O::RelNumFieldOrder, P::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> RelNumFieldOrderIdeal
```

与えられた素イデアル $P$ に対して、この関数は $\mathcal O$ の $P$-ラジカル $\sqrt{P\mathcal O}$ を返します。これは単に $\{ x \in \mathcal O \mid \exists k \in \mathbf Z_{\geq 0} \colon x^k \in P\mathcal O \}$ です。$P$ が素であることは確認されません。
