```
ExtendedSquare()
```

Extension of the Lu initialization proposed in [^herteux2020]. The state vector is extended with the squared elements of the initial state

# Equations

$$
\begin{equation}
    \vec{x} = \{x_1, x_2, \dots, x_N, x_1^2, x_2^2, \dots, x_N^2\}
\end{equation}
$$

# Examples

```jldoctest
julia> x_old = [1, 2, 3, 4, 5, 6, 7, 8, 9]
9-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
 7
 8
 9

julia> es = ExtendedSquare()
ExtendedSquare()

julia> x_new = es(x_old)
18-element Vector{Int64}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
  1
  4
  9
 16
 25
 36
 49
 64
 81

```

[^herteux2020]: Herteux, Joschka, and Christoph Räth. "Breaking symmetries of the reservoir equations in echo state networks." Chaos: An Interdisciplinary Journal of Nonlinear Science 30.12 (2020).
