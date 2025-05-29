```
jvp(fdm, f, xẋs::Tuple{Any, Any}...)
```

Compute a Jacobian-vector product with any types of arguments for which [`to_vec`](@ref) is defined. Each 2-`Tuple` in `xẋs` contains the value `x` and its tangent `ẋ`.
