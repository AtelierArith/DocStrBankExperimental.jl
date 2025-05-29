```
full_qr_solve(kktsystem, b_x, b_y, b_z, sparse_G=false)
```

KKTシステムの線形方程式を解くことによってベクトル $x$ と $y$ を計算します。ここで、KKT行列は kktsystem で与えられ、$K$ と b*x (すなわち :b*x$)、b_y (すなわち $b_y$)、b*z (すなわち :W^{-T}b*z$) はベクトルです。sparse_G を true に設定すると、G に特定のスパース構造がある場合にパフォーマンスが向上する可能性があります。

$$
K = \begin{bmatrix}
    P  & G^T   & A^T \\
    G  & -W^TW & 0   \\
    A  & 0     & 0
\end{bmatrix}
\hspace{1cm}
x = \begin{bmatrix}
\ Q_1^Tx \\
\ Q_2^Tx \\
\end{bmatrix}
$$

### 出力

ベクトル $x$ と $y$。
