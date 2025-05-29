```
insupport(d::MultivariateDistribution, x::AbstractArray)
```

If $x$ is a vector, it returns whether x is within the support of $d$. If $x$ is a matrix, it returns whether every column in $x$ is within the support of $d$.
