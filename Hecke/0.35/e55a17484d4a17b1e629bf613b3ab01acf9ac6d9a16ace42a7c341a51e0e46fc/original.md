```
pradical(O::AbsSimpleNumFieldOrder, p::{ZZRingElem|Integer}) -> AbsNumFieldOrderIdeal
```

Given a prime number $p$, this function returns the $p$-radical $\sqrt{p\mathcal O}$ of $\mathcal O$, which is just $\{ x \in \mathcal O \mid \exists k \in \mathbf Z_{\geq 0} \colon x^k \in p\mathcal O \}$. It is not checked that $p$ is prime.
