```julia
AddVector(B, b; update_func, update_func!, accepted_kwargs)

```

Represents the affine operation `w = I * v + B * b`. The update functions, `update_func[!]` update the state of `AbstractVecOrMat` `b`. See documentation of `AffineOperator` for more details.
