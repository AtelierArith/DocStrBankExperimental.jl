```
approximation_term(::CombinatorialInstance, ::CombinatorialAlgorithm)
```

Returns the approximation term for this algorithm when run on the input instance. When the problem is minimising  a function (e.g., finding the minimum-cost path), the term is defined as one constant $t \ge 0.0$  (ideally, the lowest) such that 

$f(x^\star) \leq f(x) \leq f(x^\star) + t,$

where $f(x^\star)$ is the cost of the optimum solution and $f(x)$ the one of the returned solution. On the  contrary, for a maximisation problem, the definition is reversed (with $t \ge 0.0$):

$f(x^\star) \leq f(x) \leq f(x^\star) - t.$

For an exact algorithm, the term is always $0.0$, for both minimisation and maximisation problems. 

The returned term might be constant, if the algorithm provides a constant term; if the term is not constant (i.e. instance-dependent), it may either be a worst-case value or a truly instance-dependent term. Depending on the  algorithm, this behaviour might be tuneable. 

If the algorithm has no guarantee, it should return `NaN`. 
