```
ActivationLayerP(n, σ)
```

Make an activation layer of size `n` and with activation `σ` that only changes the $p$ component. 

Performs:

$$
\begin{pmatrix}
        q \\ p
\end{pmatrix} \mapsto 
\begin{pmatrix}
        q \\ p + \mathrm{diag}(a)\sigma(q)
\end{pmatrix}.
$$

This can be recovered from [`GradientLayerP`](@ref) by setting $M$ equal to `n`, $K$ equal to $\mathbb{I}$ and $b$ equal to zero.
