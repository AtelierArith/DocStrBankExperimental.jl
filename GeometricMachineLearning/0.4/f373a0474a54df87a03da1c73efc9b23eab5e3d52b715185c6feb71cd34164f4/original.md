```
ActivationLayerQ(n, σ)
```

Make an activation layer of size `n` and with activation `σ` that only changes the $q$ component. 

Performs:

$$
\begin{pmatrix}
        q \\ p
\end{pmatrix} \mapsto 
\begin{pmatrix}
        q + \mathrm{diag}(a)\sigma(p) \\ p
\end{pmatrix}.
$$

This can be recovered from [`GradientLayerQ`](@ref) by setting $M$ equal to `n`, $K$ equal to $\mathbb{I}$ and $b$ equal to zero.
