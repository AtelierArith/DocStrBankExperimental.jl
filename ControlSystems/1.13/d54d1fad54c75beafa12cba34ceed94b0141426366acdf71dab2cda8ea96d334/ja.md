```
Simulator(P::StateSpace, u = (x,t) -> 0)
```

連続時間システムをシミュレートするために使用されます。追加情報については関数 `?solve` を参照してください。

# 使用法:

```
using OrdinaryDiffEq, Plots
dt             = 0.1
tfinal         = 20
t              = 0:dt:tfinal
P              = ss(tf(1,[2,1])^2)
K              = 5
reference(x,t) = [1.]
s              = Simulator(P, reference)
x0             = [0.,0]
tspan          = (0.0,tfinal)
sol            = solve(s, x0, tspan, Tsit5())
plot(t, s.y(sol, t)[:], lab="オープンループステップ応答")
```
