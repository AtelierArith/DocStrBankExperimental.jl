```
skew(ω::Vec{3})
```

Construct a skew-symmetric (anti-symmetric) tensor `W` from a vector `ω` as

$$
\bm{\omega} = \begin{Bmatrix}
    \omega_1 \\
    \omega_2 \\
    \omega_3
\end{Bmatrix}, \quad
\bm{W} = \begin{bmatrix}
     0         & -\omega_3 &  \omega_2 \\
     \omega_3 & 0          & -\omega_1 \\
    -\omega_2 &  \omega_1 &  0
\end{bmatrix}
$$

# Examples

```jldoctest
julia> skew(Vec(1,2,3))
3×3 Tensor{Tuple{3, 3}, Int64, 2, 9}:
  0  -3   2
  3   0  -1
 -2   1   0
```
