```
swinnerton_dyer(n::Int, x::ZZPolyRingElem)
```

Return the Swinnerton-Dyer polynomial $S_n$, defined as the integer polynomial $S_n = \prod (x \pm \sqrt{2} \pm \sqrt{3} \pm \sqrt{5} \pm \ldots \pm \sqrt{p_n})$ where $p_n$ denotes the $n$-th prime number and all combinations of signs are taken. This polynomial has degree $2^n$ and is irreducible over the integers (it is the minimal polynomial of $\sqrt{2} + \ldots + \sqrt{p_n}$).
