```julia
AddVector(b; update_func, update_func!, accepted_kwargs)

```

Represents the affine operation `w = I * v + I * b`. The update functions, `update_func[!]` update the state of `AbstractVecOrMat` `b`. See documentation of `AffineOperator` for more details.
