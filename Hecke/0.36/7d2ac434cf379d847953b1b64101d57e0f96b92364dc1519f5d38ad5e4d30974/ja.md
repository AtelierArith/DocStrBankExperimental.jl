```
minkowski_matrix(O::AbsNumFieldOrder, abs_tol::Int = 64) -> ArbMatrix
```

$$
\mathcal O
$$

のミンコフスキー行列を返します。したがって、$\mathcal O$の次数が$d$である場合、結果は$\operatorname{Mat}_{d\times d}(\mathbf R)$の行列です。行列のエントリは、半径が`2^-abs_tol`未満の`ArbFieldElem`型の実ボールです。
