```
spdiag(m::Integer, pair::Pair...)
```

Constructs a square $m\times m$ [`SparseTensor`](@ref) from pairs of the form 

```
offset => array 
```

# Example

Suppose we want to construct a $10\times 10$ tridiagonal matrix, where the lower off-diagonals are all -2,  the diagonals are all 2, and the upper off-diagonals are all 3, the corresponding Julia code is 

```julia
spdiag(10, -1=>-2*ones(9), 0=>2*ones(10), 1=>3ones(9))
```
