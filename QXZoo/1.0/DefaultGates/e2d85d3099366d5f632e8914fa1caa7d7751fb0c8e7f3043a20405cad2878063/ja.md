```
r_y(q_target::Int, theta::Number)
```

ターゲットキュービットに適用される単一キュービット R_y(θ) ゲートコール (GateCall1) を生成します。

# 例

```julia-repl
julia> QXZoo.DefaultGates.r_y(3,pi/2)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbolP(:r_y, 0, false, 1.5707963267948966), 3)
```
