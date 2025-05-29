```
Fμν(x, laser)
```

[電磁テンソル](https://en.wikipedia.org/wiki/Electromagnetic_tensor) $F$ を、指定された時空4ベクトル `x` における共変行列形式で計算します。$x = (x^0 ≡ ct, x^1, x^2, x^3)$ の規約が使用されています。

$$
F^{μν} =
\left[\begin{array}{cccc}
    0   &  -E_x / c  & -E_y / c & -E_z / c \\
E_x / c &       0    &   -B_z   &    B_y   \\
E_y / c &      B_z   &     0    &   -B_x   \\
E_z / c &     -B_y   &    B_z   &     0
\end{array}\right]
$$
