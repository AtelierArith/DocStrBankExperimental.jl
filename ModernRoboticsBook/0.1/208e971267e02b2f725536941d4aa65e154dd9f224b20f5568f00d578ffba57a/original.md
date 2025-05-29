```
TestIfSE3(mat)
```

Returns true if mat is close to or on the manifold SE(3).

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> TestIfSE3([1.0 0.0 0.0 1.2; 0.0 0.1 -0.95 1.5; 0.0 1.0 0.1 -0.9; 0.0 0.0 0.1 0.98])
false
```
