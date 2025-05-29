```
NLAT3()
```

Implements the T₃ transformation algorithm as detailed in [^Chattopadhyay]. This algorithm modifies the reservoir's states by multiplying each odd-indexed row (beginning from the second row) with the product of the immediately preceding and the immediately following rows.

$$
\tilde{r}_{i,j} =
\begin{cases}
r_{i,j-1} \times r_{i,j+1}, & \text{if } j > 1 \text{ is odd}; \\
r_{i,j}, & \text{if } j = 1 \text{ or even.}
\end{cases}
$$

# Example

```jldoctest
julia> nlat = NLAT3()
NLAT3()

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
  3
  3
 15
  5
 35
  7
 63
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
   1    2    3
   4    5    6
  40   55   72
  10   11   12
 160  187  216
  16   17   18
  19   20   21

```

[^Chattopadhyay]: Chattopadhyay, Ashesh, et al. "Data-driven predictions of a multiscale Lorenz 96 chaotic system using machine-learning methods: reservoir computing, artificial neural network, and long short-term memory network." (2019).
