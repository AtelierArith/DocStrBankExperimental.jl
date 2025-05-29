```
trred_matrix(O::AlgssRelOrd) -> MatElem
```

$$
O
$$

の縮小トレース行列$M$を返します。すなわち、`M[i, j] = trred(b[i]*b[j])`であり、ここで$b$は$O$の基底です。
