```
DistanceToSO3(mat)
```

Returns the Frobenius norm to describe the distance of mat from the SO(3) manifold.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> DistanceToSO3([1.0 0.0 0.0; 0.0 0.1 -0.95; 0.0 1.0 0.1])
0.08835298523536149
```
