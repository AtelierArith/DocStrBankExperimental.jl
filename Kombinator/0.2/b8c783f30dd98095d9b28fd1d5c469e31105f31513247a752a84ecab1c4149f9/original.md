```
approximation_ratio(::CombinatorialInstance, ::CombinatorialAlgorithm)
```

Returns the approximation ratio for this algorithm when run on the input instance. When the problem is minimising  a function (e.g., finding the minimum-cost path), the ratio is defined as one constant $r \le 1.0$ (ideally, the lowest) such that 

$f(x^\star) \leq f(x) \leq r \cdot f(x^\star),$

where $f(x^\star)$ is the cost of the optimum solution and $f(x)$ the one of the returned solution. On the  contrary, for a maximisation problem, the definition is reversed (with $r \le 1.0$):

$r \cdot f(x^\star) \geq f(x) \geq f(x^\star).$

For an exact algorithm, the ratio is always $1.0$, for both minimisation and maximisation problems. 

The returned ratio might be constant, if the algorithm provides a constant ratio; if the ratio is not constant (i.e. instance-dependent), it may either be a worst-case value or a truly instance-dependent ratio. Depending on the  algorithm, this behaviour might be tuneable. 

If the algorithm has no guarantee, it should return `NaN`. 
