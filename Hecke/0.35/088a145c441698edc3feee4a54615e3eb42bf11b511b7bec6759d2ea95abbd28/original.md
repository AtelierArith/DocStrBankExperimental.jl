```
elementary_divisors(G::FinGenAbGroup) -> Vector{ZZRingElem}
```

Given $G$, return the elementary divisors of $G$, that is, the unique non-negative integers $e_1,\dotsc,e_k$ with $e_i \mid e_{i + 1}$ and $e_i\neq 1$ such that $G \cong \mathbf{Z}/e_1\mathbf{Z} \times \dotsb \times \mathbf{Z}/e_k\mathbf{Z}$.
