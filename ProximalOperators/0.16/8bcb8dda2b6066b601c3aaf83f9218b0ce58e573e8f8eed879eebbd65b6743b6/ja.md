```
HuberLoss(ρ=1, μ=1)
```

関数を返します

$$
f(x) = \begin{cases}
    \tfrac{μ}{2}\|x\|^2 & \text{if}\ \|x\| ⩽ ρ \\
    ρμ(\|x\| - \tfrac{ρ}{2}) & \text{otherwise},
\end{cases}
$$

ここで `ρ` と `μ` は正のパラメータです。
