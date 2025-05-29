```
NLAT2()
```

`NLAT2` implements the T₂ transformation algorithm as defined in [^Chattopadhyay]. This transformation algorithm modifies the reservoir states by multiplying each odd-indexed row (starting from the second row) with the product of its two preceding rows.

$$
\tilde{r}_{i,j} =
\begin{cases}
    r_{i,j-1} \times r_{i,j-2}, & \text{if } j > 1 \text{ is odd}; \\
    r_{i,j}, & \text{if } j \text{ is 1 or even}.
\end{cases}
$$

# Example

```jldoctest
julia> nlat = NLAT2()
NLAT2()

julia> x_old = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
10-element Vector{Int64}:
 0
 1
 2
 3
 4
 5
 6
 7
 8
 9

julia> n_new = nlat(x_old)
10-element Vector{Int64}:
  0
  1
  0
  3
  6
  5
 20
  7
 42
  9

julia> mat_old = [1  2  3;
                   4  5  6;
                   7  8  9;
                  10 11 12;
                  13 14 15;
                  16 17 18;
                  19 20 21]
7×3 Matrix{Int64}:
  1   2   3
  4   5   6
  7   8   9
 10  11  12
 13  14  15
 16  17  18
 19  20  21

julia> mat_new = nlat(mat_old)
7×3 Matrix{Int64}:
  1   2    3
  4   5    6
  4  10   18
 10  11   12
 70  88  108
 16  17   18
 19  20   21

```

[^Chattopadhyay]: Chattopadhyay, Ashesh, et al. "Data-driven prediction of a multi-scale Lorenz 96 chaotic system using a hierarchy of deep learning methods: Reservoir computing, ANN, and RNN-LSTM." (2019).
