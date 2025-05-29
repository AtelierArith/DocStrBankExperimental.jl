```
standardise(X::FloatVector)
standardise(X::FloatMatrix)
standardise(X::JVector{Float64})
standardise(X::JMatrix{Float64})
```

Standardise `X`.

# Examples

```jldoctest
julia> standardise([1.0; 1.5; 2.0; 2.5; 3.0])
5-element Array{Float64,1}:
 -1.2649110640673518
 -0.6324555320336759
  0.0
  0.6324555320336759
  1.2649110640673518

julia> standardise([1.0 3.5 1.5 4.0 2.0; 4.5 2.5 5.0 3.0 5.5])
2×5 Array{Float64,2}:
 -1.08173    0.849934  -0.695401   1.23627   -0.309067
  0.309067  -1.23627    0.695401  -0.849934   1.08173
```
