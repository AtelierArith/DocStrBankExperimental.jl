```
TestIfSO3(mat)
```

Returns true if mat is close to or on the manifold SO(3).

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> TestIfSO3([1.0 0.0 0.0; 0.0 0.1 -0.95; 0.0 1.0 0.1])
false
```
