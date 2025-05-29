```
phase_shift(phi)
```

位相シフト `phi` を適用する `DiagonalOperator` を返します。

`DiagonalOperator` は次のように定義されます：

$$
P(\phi) = \begin{bmatrix}
    1 & 0 \\[0.5em]
    0 & e^{i\phi}
\end{bmatrix}.
$$
