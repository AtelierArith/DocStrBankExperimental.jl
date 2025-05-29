```
joint_entropy(priors :: AbstractVector, conditionals :: AbstractMatrix) :: Float64
```

Returns the entropy for the union of pdf $P(x,y)$. The joint entropy is the [`shannon_entropy`](@ref) of the joint probability distribution:

$$
S(X,Y) = - \sum_{x,y} p(x,y) \log_2(p(x,y))
$$
