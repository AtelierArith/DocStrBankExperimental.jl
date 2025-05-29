```
TrapezoidalRule
```

台形法を用いて積分を評価するための構造体。

サンプルデータを用いた例：

```julia
using Integrals
f = x -> x^2
x = range(0, 1, length=20)
y = f.(x)
problem = SampledIntegralProblem(y, x)
method = TrapezoidalRule()
solve(problem, method)
```
