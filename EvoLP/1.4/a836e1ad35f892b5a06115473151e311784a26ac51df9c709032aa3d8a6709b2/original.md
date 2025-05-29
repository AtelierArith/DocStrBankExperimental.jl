```
jumpk(x; k=6)
```

The **JumpK** function is a modification of the [`onemax`](@ref) function, with a valley of size $k$ right before the maximum. The only way for a hill climber to reach the maximum is with a *perfect flip* of $k$ bits, which is considered extremely difficult.

$$
\text{JUMP}_k(x) = \begin{cases}
\lVert{x}\rVert_1 & \quad \text{if } \lVert x \rVert_1 \in [0..n-k] \cup \{n\},\\
-\lVert x \rVert_1 & \quad \text{otherwise}
\end{cases}
$$

where $\lVert x \rVert_1 = \sum_{i=1}^n x_i$ is the number of 1-bits in $x \in \{0, 1\}^n$.
