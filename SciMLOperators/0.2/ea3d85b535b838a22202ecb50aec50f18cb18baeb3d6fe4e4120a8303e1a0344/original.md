```julia
AddVector(b; update_func, update_func!, accepted_kwargs)

```

Represents the affine operation `v = I * u + I * b`. The update functions, `update_func[!]` update the state of `AbstractVecOrMat` `b`. see documentation of `AffineOperator` for more details.
