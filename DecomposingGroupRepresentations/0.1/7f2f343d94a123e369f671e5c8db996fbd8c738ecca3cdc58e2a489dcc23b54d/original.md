```
chevalley_basis(::AbstractLieAlgebra)
```

Returns the Chevalley basis of the given Lie algebra. For example, for the Lie algebra $\mathfrak{so}(3, \mathbb{C})$ returns 

$$
\left\{ 
\underbrace{\begin{bmatrix} 0 & 0 & -1 \\ 0 & 0 & -i \\ 1 & i & 0 \end{bmatrix}}_{J_+},
\underbrace{\begin{bmatrix} 0 & 0 & 1 \\ 0 & 0 & -i \\ -1 & i & 0 \end{bmatrix}}_{J_-},
\underbrace{\begin{bmatrix} 0 & -i & 0 \\ i & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix}}_{J_3}
\right\}
$$

with the commutation relations

$$
\begin{aligned}
[J_3, J_+] &= J_+ \\
[J_3, J_-] &= -J_- \\
[J_+, J_-] &= 2J_3
\end{aligned}
$$
