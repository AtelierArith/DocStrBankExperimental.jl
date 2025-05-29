dummycreate(inputmat::Vector)

`dummycreate` allows to create a matrix of zeros and ones from a vector of groups. The input argument `inputmat` must be a `Vector`. 

# Examples

```julia-repl
julia> dummycreate([1.0, 2.0])

2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

dummycreate(['a', 'b'])

2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

dummycreate([1, 'a', 'b', 1])

4×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
 1.0  0.0  0.0
```
