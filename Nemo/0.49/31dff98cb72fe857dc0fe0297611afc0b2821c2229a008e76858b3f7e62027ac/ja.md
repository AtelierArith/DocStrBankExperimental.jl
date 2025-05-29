```
theta_qexp(e::Int, n::Int, x::ZZPolyRingElem)
```

Jacobi theta関数を$r$乗した$q$-展開の長さ$n$を返します。すなわち、$\vartheta(q)^r$であり、ここで$\vartheta(q) = 1 + \sum_{k=1}^{\infty} q^{k^2}$です。
