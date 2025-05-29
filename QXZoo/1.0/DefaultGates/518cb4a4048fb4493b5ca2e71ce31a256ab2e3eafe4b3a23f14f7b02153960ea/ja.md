```
r_x(q_target::Int, theta::Number)
```

ターゲットキュービットに適用される単一キュービット R_x(θ) ゲートコール (GateCall1)

# 例

```julia-repl
julia> QXZoo.DefaultGates.r_x(3,pi/2)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbolP(:r_x, 0, false, 1.5707963267948966), 3)
```
