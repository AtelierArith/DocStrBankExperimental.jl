```
Infomax(; orthogonal = false)
```

The *Infomax* rotation method.

## Details

The *Infomax* method maximizes the mutual information between the variables and factors:

$$
\begin{aligned}
Q_{\mathrm{Infomax}}(Λ) =& \left(∑_{i,j} λ_{i,j}²\right)^{-1} \left(
    - ∑_{i,j} λ_{i,j}² \log λ_{i,j}²
    + ∑_{i=1}^p \left(∑_{j=1}^k λ_{i,j}²\right) \log ∑_{j=1}^k λ_{i,j}² + \right. \\
    & \hspace{8em} \left.
    + ∑_{j=1}^k \left(∑_{i=1}^p λ_{i,j}²\right) \log ∑_{i=1}^p λ_{i,j}²
    - \log k
    \right).
\end{aligned}
$$

## Keyword arguments

  * `orthogonal`: If `orthogonal = true` an orthogonal rotation is performed, an oblique  rotation otherwise. (default: `false`)
