```
conditional_entropy(priors::AbstractVector, conditionals::AbstractMatrix) :: Float64
```

Returns the conditional entropy for the system with specified `priors` $p(x)$ and `conditionals` $p(y|x)$:

$$
S(Y|X) = - \sum_{x,y} p(x,y)\log_2\left(\frac{p(y|x)}{p(x)}\right)
$$
