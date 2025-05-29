```
HuberLoss(ρ=1, μ=1)
```

Return the function

$$
f(x) = \begin{cases}
    \tfrac{μ}{2}\|x\|^2 & \text{if}\ \|x\| ⩽ ρ \\
    ρμ(\|x\| - \tfrac{ρ}{2}) & \text{otherwise},
\end{cases}
$$

where `ρ` and `μ` are positive parameters.
