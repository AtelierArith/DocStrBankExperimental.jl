```
find_arb!(Δ, Λ, cfmm, v)
```

Solves the arbitrage problem for `cfmm` given price vector `v`,

$$
\begin{array}{ll}
\text{minimize} & \nu^T(\Lambda - \Delta) \\
\text{subject to} & \varphi(R + \gamma\Delta - \Lambda) = \varphi(R) \\
& \Delta, \Lambda \geq 0.
\end{array}
$$

Overwrites the variables `Δ` and `Λ`.
