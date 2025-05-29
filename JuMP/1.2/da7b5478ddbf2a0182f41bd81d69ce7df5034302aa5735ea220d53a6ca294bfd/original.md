```
SkewSymmetricMatrixSpace()
```

Use in the [`@variable`](@ref) macro to constrain a matrix of variables to be skew-symmetric.

## Examples

```jldoctest; setup=:(model = Model())
@variable(model, Q[1:2, 1:2] in SkewSymmetricMatrixSpace())
```
