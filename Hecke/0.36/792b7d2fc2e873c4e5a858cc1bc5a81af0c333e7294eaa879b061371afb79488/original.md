```
conjugates(a::AbsSimpleNumFieldElem, C::qAdicConj, n::Int = 10; flat::Bool = false, all:Bool = true) -> []
```

Returns an array of the $q$-adic conjugates of $a$: Let $p Z_K = \prod P_i$ for the maximal order $Z_K$ of the parent of $a$. Then $K \otimes Q_p = \prod K_{P_i}$. For each of the $P_i$ a $q$-adic (unramifed) extension $K_{P_i}$ of $Q_p$ is computed, sth. $a$ has $\deg P_i = \deg K_{P_i}$ many conjugates in $K_{P_i}$. If `all = true` and `flat = false`, the default, then all $n$ conjugates are returned. If `all = false`, then for each $P_i$ only one conjugate is returned, the others could be computed using automorphisms (the Frobenius). If `flat = true`, then instead of the conjugates, only the $p$-adic coefficients are returned.
