```
c_r_x(q_target::Int, q_ctrl::Int, theta::Number)
```

x軸周りの制御回転を生成します (exp(-iθx/2)) GateCall (GateCall2)、ターゲット `q_target` に適用される `q_ctrl` インデックスに基づいて制御されます。

# 例

```julia-repl
julia> QXZoo.DefaultGates.c_r_x( 0, 1, pi/2)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbolP(:c_r_x, 0, false, 1.5707963267948966), 0, 1, nothing)
```
