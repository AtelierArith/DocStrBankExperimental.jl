```
show_psi(N::Integer, B::Int)
show_psi(N::ZZRingElem, B::Int)
```

Uses \code{psi*lower} and \code{psi*upper} to find intervals for $\psi(2^i, B)$ to be in for $0\le i\le \log_2(N)$. Where $\psi(N, B) = \#\{1\le i\le N | \text{$i$ is $B$-smooth}}$
