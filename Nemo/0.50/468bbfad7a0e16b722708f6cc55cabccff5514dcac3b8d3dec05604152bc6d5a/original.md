```
reconstruct(a::ZZRingElem, m::ZZRingElem, N::ZZRingElem, D::ZZRingElem)
```

Attempt to return a rational number $n/d$ such that $0 \leq |n| \leq N$ and $0 < d \leq D$ such that $2 N D < m$, gcd$(n, d) = 1$, and $a \equiv nd^{-1} \pmod{m}$.

Returns a tuple (`success`, `n/d`), where `success` signals the success of reconstruction.

The behaviour is undefined if $a$ is negative or larger than $m$.
