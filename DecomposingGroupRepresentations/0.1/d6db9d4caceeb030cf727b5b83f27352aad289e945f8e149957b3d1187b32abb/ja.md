```
basis(::AbstractLieAlgebra)
```

与えられたリー代数の基底を返します。例えば、リー代数 $\mathfrak{so}(3, \mathbb{C})$ は反対称行列から成り、その（標準的な）基底は次の行列で与えられます。

$$
\left\{ 
\begin{bmatrix} 0 & 0 & 0 \\ 0 & 0 & -1 \\ 0 & 1 & 0 \end{bmatrix},
\begin{bmatrix} 0 & 0 & 1 \\ 0 & 0 & 0 \\ -1 & 0 & 0 \end{bmatrix},
\begin{bmatrix} 0 & -1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix}
\right\}
$$
