```
Infomax(; orthogonal = false)
```

*Infomax*回転法。

## 詳細

*Infomax*法は、変数と因子間の相互情報量を最大化します：

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

## キーワード引数

  * `orthogonal`: `orthogonal = true`の場合、直交回転が行われ、それ以外の場合は斜め回転が行われます。（デフォルト：`false`）
