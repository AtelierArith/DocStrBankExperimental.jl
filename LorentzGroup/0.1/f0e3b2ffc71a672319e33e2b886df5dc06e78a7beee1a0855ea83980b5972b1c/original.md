```
comoving(u; normalize=true)
```

Creates the boost into the comoving frame of $u$ as a [`LorMatrix`](@ref).  This is given by

$$
{\Lambda^\mu}_\nu=\left(\begin{array}{cc}
    {\delta^i}_j + \frac{u^i u_j}{u_4 + 1} & -u_j \\
    -u^i & u_4
\end{array}\right)
$$

If `normalize=true`, $u$ will be normalized.  If `normalize=false`, no check will be performed so that the result is undefined if $u$ is not normalized.
