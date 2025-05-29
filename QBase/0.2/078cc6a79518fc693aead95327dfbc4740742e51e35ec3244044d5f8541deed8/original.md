```
mutual_information(
    priors :: AbstractVector,
    conditionals :: AbstractMatrix
) :: Float64
```

The entropy of the overlap between $p(x)$ and $p(y)$. The mutual information is directly computed from the [`shannon_entropy`](@ref) and [`joint_entropy`](@ref):

$$
I(X : Y) = S(X) + S(Y) - S(X,Y)
$$
