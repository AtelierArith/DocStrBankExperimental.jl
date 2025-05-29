# Extended help

```
σ(d::AbstractVector, H::Hyperplane)
```

### Output

A support vector in the given direction, which is only defined in the following two cases:

1. The direction has norm zero.
2. The direction is the hyperplane's normal direction or its opposite direction.

In all cases, any point on the hyperplane is a solution. Otherwise this function throws an error.
