```
ladiv(A, B, C, D) -> (P, Q)
```

実数算術で複素数の除算を行います。

$$
P + iQ = \displaystyle\frac{A+iB}{C+iD}
$$

不必要なオーバーフローを避けるために。LAPACKサブルーチンDLADIV/SLADIVへのインターフェース。
