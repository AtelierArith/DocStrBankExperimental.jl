```
simplex_grid(m, n)
```

Construct an array consisting of the integer points in the (m-1)-dimensional simplex $\{x \mid x_1 + \cdots + x_m = n, x_i \geq 0\}$, or equivalently, the m-part compositions of n, which are listed in lexicographic order. The total number of the points (hence the length of the output array) is L = (n+m-1)!/(n!*(m-1)!) (i.e., (n+m-1) choose (m-1)).

# Arguments

  * `m::Int` : Dimension of each point. Must be a positive integer.
  * `n::Int` : Number which the coordinates of each point sum to. Must            be a nonnegative integer.

# Returns

  * `out::Matrix{Int}` : Array of shape (m, L) containing the integer                      points in the simplex, aligned in lexicographic                      order.

# Notes

A grid of the (m-1)-dimensional *unit* simplex with n subdivisions along each dimension can be obtained by `simplex_grid(m, n) / n`.

# Examples

```julia
julia> simplex_grid(3, 4)
3×15 Matrix{Int64}:
 0  0  0  0  0  1  1  1  1  2  2  2  3  3  4
 0  1  2  3  4  0  1  2  3  0  1  2  0  1  0
 4  3  2  1  0  3  2  1  0  2  1  0  1  0  0
```

# References

A. Nijenhuis and H. S. Wilf, Combinatorial Algorithms, Chapter 5,    Academic Press, 1978.
