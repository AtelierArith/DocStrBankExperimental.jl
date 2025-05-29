```
DistanceToSE3(mat)
```

Returns the Frobenius norm to describe the distance of mat from the SE(3) manifold.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> DistanceToSE3([1.0 0.0 0.0 1.2; 0.0 0.1 -0.95 1.5; 0.0 1.0 0.1 -0.9; 0.0 0.0 0.1 0.98])
0.13493053768513638
```
