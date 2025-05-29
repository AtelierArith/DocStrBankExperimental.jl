```
SimpsonsRule
```

構造体で、`AbstractRange`（等間隔の点）上でシンプソンの合成1/3-3/8ルールを使用して積分を評価し、非等間隔グリッドに対してシンプソンの合成1/3ルールを使用します。

等間隔データの例：

```julia
using Integrals
f = x -> x^2
x = range(0, 1, length=20)
y = f.(x)
problem = SampledIntegralProblem(y, x)
method = SimpsonsRule()
solve(problem, method)
```
