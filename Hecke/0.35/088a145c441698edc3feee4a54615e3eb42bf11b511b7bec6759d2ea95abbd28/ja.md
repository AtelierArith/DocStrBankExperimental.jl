```
elementary_divisors(G::FinGenAbGroup) -> Vector{ZZRingElem}
```

与えられた $G$ に対して、$G$ の基本因子を返します。すなわち、$e_i \mid e_{i + 1}$ かつ $e_i \neq 1$ である一意の非負整数 $e_1,\dotsc,e_k$ であって、$G \cong \mathbf{Z}/e_1\mathbf{Z} \times \dotsb \times \mathbf{Z}/e_k\mathbf{Z}$ となるものです。
