```
chevalley_basis(::AbstractLieAlgebra)
```

与えられたリー代数のシェバレーバイスタを返します。例えば、リー代数 $\mathfrak{so}(3, \mathbb{C})$ の場合、次のように返されます。

$$
\left\{ 
\underbrace{\begin{bmatrix} 0 & 0 & -1 \\ 0 & 0 & -i \\ 1 & i & 0 \end{bmatrix}}_{J_+},
\underbrace{\begin{bmatrix} 0 & 0 & 1 \\ 0 & 0 & -i \\ -1 & i & 0 \end{bmatrix}}_{J_-},
\underbrace{\begin{bmatrix} 0 & -i & 0 \\ i & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix}}_{J_3}
\right\}
$$

交換関係は次の通りです。

$$
\begin{aligned}
[J_3, J_+] &= J_+ \\
[J_3, J_-] &= -J_- \\
[J_+, J_-] &= 2J_3
\end{aligned}
$$
