```
demean(X::FloatVector)
demean(X::FloatMatrix)
demean(X::JVector{Float64})
demean(X::JMatrix{Float64})
```

`X`の平均を引く。

# 例

```jldoctest
julia> demean([1.0; 1.5; 2.0; 2.5; 3.0])
5-element Array{Float64,1}:
 -1.0
 -0.5
  0.0
  0.5
  1.0

julia> demean([1.0 3.5 1.5 4.0 2.0; 4.5 2.5 5.0 3.0 5.5])
2×5 Array{Float64,2}:
 -1.4   1.1  -0.9   1.6  -0.4
  0.4  -1.6   0.9  -1.1   1.4
```
