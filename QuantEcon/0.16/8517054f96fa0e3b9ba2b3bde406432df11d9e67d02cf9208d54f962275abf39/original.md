```
SimplexGrid
```

Iterator version of `simplex_grid`, i.e., iterator that iterates over the integer points in the (m-1)-dimensional simplex $\{x \mid x_1 + \cdots + x_m = n, x_i \geq 0\}$, or equivalently, the m-part compositions of n, in lexicographic order.

# Fields

  * `m::Int` : Dimension of each point. Must be a positive integer.
  * `n::Int` : Number which the coordinates of each point sum to. Must            be a nonnegative integer.

# Examples

```julia
julia> sg = SimplexGrid(3, 4);

julia> for x in sg
           @show x
       end
x = [0, 0, 4]
x = [0, 1, 3]
x = [0, 2, 2]
x = [0, 3, 1]
x = [0, 4, 0]
x = [1, 0, 3]
x = [1, 1, 2]
x = [1, 2, 1]
x = [1, 3, 0]
x = [2, 0, 2]
x = [2, 1, 1]
x = [2, 2, 0]
x = [3, 0, 1]
x = [3, 1, 0]
x = [4, 0, 0]
```
