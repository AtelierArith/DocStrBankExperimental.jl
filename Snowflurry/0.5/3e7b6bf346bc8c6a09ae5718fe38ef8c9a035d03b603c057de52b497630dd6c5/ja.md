```
root_zz()
```

2回連続して適用されると、最初のキュービットに対して$-\frac{\pi}{2}$の回転を、2番目のキュービットに対して$\frac{\pi}{2}$の回転を適用する`DiagonalOperator`を返します。

`DiagonalOperator`は次のように定義されます：

$$
R_{ZZ} = \begin{bmatrix}
    1-i & 0 & 0 & 0 \\
    0 & 1+i & 0 & 0 \\
    0 & 0 & 1+i & 0 \\
    0 & 0 & 0 & 1-i \\
\end{bmatrix}.
$$
