```
trred_matrix(O::AlgAssAbsOrd) -> ZZMatrix
```

$$
O
$$

の縮約トレース行列$M$を返します。すなわち、`M[i, j] = trred(b[i]*b[j])`であり、ここで$b$は$O$の基底です。
