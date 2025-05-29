```
c_r_y(q_target::Int, q_ctrl::Int, theta::Number)
```

y軸周りの制御回転 (exp(iθy/2)) GateCall (GateCall2) を生成し、ターゲット `q_target` に適用される `q_ctrl` インデックスで制御されます。

# 例

```julia-repl
julia> QXZoo.DefaultGates.c_r_y( 0, 1, pi/3)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbolP(:c_r_y, 0, false, 1.0471975511965976), 0, 1, nothing)
```
