```
simplex_index(x, m, n)
```

Return the index of the point x in the lexicographic order of the integer points of the (m-1)-dimensional simplex $\{x \mid x_0 + \cdots + x_{m-1} = n\}$.

# Arguments

  * `x::Vector{Int}` : Integer point in the simplex, i.e., an array of                    m nonnegative integers that sum to n.
  * `m::Int` : Dimension of each point. Must be a positive integer.
  * `n::Int` : Number which the coordinates of each point sum to. Must be a            nonnegative integer.

# Returns

  * `idx::Int` : Index of x.
