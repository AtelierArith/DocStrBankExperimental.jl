```
PartialSquare(eta)
```

状態の部分的な二乗を、[^\barbosa2021]で説明されているように実装します。

# 方程式

$$
    \begin{equation}
    g(r_i) =
    \begin{cases} 
        r_i^2, & \text{if } i \leq \eta_r N, \\
        r_i, & \text{if } i > \eta_r N.
    \end{cases}
    \end{equation}
$$

# 例

```jldoctest julia> ps = PartialSquare(0.6) PartialSquare(0.6)

julia> x_old = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] 10-element Vector{Int64}:  0  1  2  3  4  5  6  7  8  9

julia> x*new = ps(x*old) 10-element Vector{Int64}:   0   1   4   9  16  25   6   7   8   9

[^barbosa2021]: Barbosa, Wendson AS, et al. "Symmetry-aware reservoir computing." Physical Review E 104.4 (2021): 045307.
```
