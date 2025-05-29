```
full_qr_solve(kktsystem, b_x, b_y, b_z, sparse_G=false)
```

Calculates the vectors $x$ and $y$ by solving the KKT system of linear equations where the KKT matrix is given by kktsystem, $K$ and b_x (i.e. $b_x$), b_y (i.e. $b_y$), b_z (i.e. $W^{-T}b_z$) are vectors. Setting sparse_G to true may improve performance if G has a particular sparsity structure.

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

### Output

The vectors $x$ and $y$.
