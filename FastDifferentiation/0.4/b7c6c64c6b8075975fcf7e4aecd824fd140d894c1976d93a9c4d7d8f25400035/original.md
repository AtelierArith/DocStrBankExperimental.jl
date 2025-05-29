```
hessian_times_v(term::Node, partial_variables::AbstractVector{<:Node})
```

Computes Hessian times a vector v without forming the Hessian matrix. Useful when the Hessian would be impractically large.
