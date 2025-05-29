```
conditional_entropy(priors::AbstractVector, conditionals::AbstractMatrix) :: Float64
```

指定された `priors` $p(x)$ と `conditionals` $p(y|x)$ を持つシステムの条件付きエントロピーを返します：

$$
S(Y|X) = - \sum_{x,y} p(x,y)\log_2\left(\frac{p(y|x)}{p(x)}\right)
$$
