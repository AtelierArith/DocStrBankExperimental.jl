```
  pradical(O::RelNumFieldOrder, P::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> RelNumFieldOrderIdeal
```

Given a prime ideal $P$, this function returns the $P$-radical $\sqrt{P\mathcal O}$ of $\mathcal O$, which is just $\{ x \in \mathcal O \mid \exists k \in \mathbf Z_{\geq 0} \colon x^k \in P\mathcal O \}$. It is not checked that $P$ is prime.
