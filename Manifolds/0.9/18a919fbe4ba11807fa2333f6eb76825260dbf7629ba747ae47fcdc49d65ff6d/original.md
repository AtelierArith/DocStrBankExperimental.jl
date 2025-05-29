```
project(::Flag, p, X)
```

Project vector `X` in the Euclidean embedding to the tangent space at point `p` on [`Flag`](@ref) manifold. The formula reads [YeWongLim:2021](@cite):

$$
Y_i = X_i - (p_i p_i^{\mathrm{T}}) X_i + \sum_{j \neq i} p_j X_j^{\mathrm{T}} p_i
$$

for $i$ from 1 to $d$ where the resulting vector is $Y = [Y_1, Y_2, …, Y_d]$ and $X = [X_1, X_2, …, X_d]$, $p = [p_1, p_2, …, p_d]$ are decompositions into basis vector matrices for consecutive subspaces of the flag.
