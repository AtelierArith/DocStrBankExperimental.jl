```
psi_lower(N::Integer, B::Int, a::Int = 776) -> Vector{Int}, ZZAbsPowerSeriesRingElem
psi_lower(N::ZZRingElem, B::Int, a::Int = 776) -> Vector{Int}, ZZAbsPowerSeriesRingElem
```

Uses Bernstein's ideas: https://cr.yp.to/papers/psi.pdf to compute lower bounds on the psi function counting smooth numbers. An array $L$ is returned s.th. $\psi(2^{i-1}, B) \ge L_i$ for $1\le i\le \rceil \log_2(B)\lceil$. The second return value is Bernstein's power series.

The optional other parameter $a$ controls the precision of the result, it defaults to 776.
