```
basis(::AbstractLieAlgebra)
```

Returns a basis of the given Lie algebra. For example, the Lie algebra $\mathfrak{so}(3, \mathbb{C})$, consists of skew-symmetric matrices and hence its (standard) basis is given by the matrices

$$
\left\{ 
\begin{bmatrix} 0 & 0 & 0 \\ 0 & 0 & -1 \\ 0 & 1 & 0 \end{bmatrix},
\begin{bmatrix} 0 & 0 & 1 \\ 0 & 0 & 0 \\ -1 & 0 & 0 \end{bmatrix},
\begin{bmatrix} 0 & -1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix}
\right\}
$$
