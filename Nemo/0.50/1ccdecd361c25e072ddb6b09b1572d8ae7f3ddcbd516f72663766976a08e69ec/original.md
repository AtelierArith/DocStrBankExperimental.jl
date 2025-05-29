```
eta_qexp(e::Int, n::Int, x::ZZPolyRingElem)
```

Return the $q$-expansion to length $n$ of the Dedekind eta function (without the leading factor $q^{1/24}$) raised to the power $r$, i.e. $(q^{-1/24} \eta(q))^r = \prod_{k=1}^{\infty} (1 - q^k)^r$. In particular, $r = -1$ gives the generating function of the partition function $p(k)$, and $r = 24$ gives, after multiplication by $q$, the modular discriminant $\Delta(q)$ which generates the Ramanujan tau function $\tau(k)$.
