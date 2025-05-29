```
TrapezoidalRule
```

Struct for evaluating an integral via the trapezoidal rule.

Example with sampled data:

```julia
using Integrals
f = x -> x^2
x = range(0, 1, length=20)
y = f.(x)
problem = SampledIntegralProblem(y, x)
method = TrapezoidalRule()
solve(problem, method)
```
