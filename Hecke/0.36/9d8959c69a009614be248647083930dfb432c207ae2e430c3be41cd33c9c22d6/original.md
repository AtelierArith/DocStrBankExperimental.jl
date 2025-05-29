```
poverorder(O::AbsSimpleNumFieldOrder, p::ZZRingElem) -> AbsSimpleNumFieldOrder
poverorder(O::AbsSimpleNumFieldOrder, p::Integer) -> AbsSimpleNumFieldOrder
```

This function tries to find an order that is locally larger than $\mathcal O$ at the prime $p$: If $p$ divides the index $[ \mathcal O_K : \mathcal O]$, this function will return an order $R$ such that $v_p([ \mathcal O_K : R]) < v_p([ \mathcal O_K : \mathcal O])$. Otherwise $\mathcal O$ is returned.
