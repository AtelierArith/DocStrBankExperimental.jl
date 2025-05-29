```
c_r_z(q_target::Int, q_ctrl::Int, theta::Number)
```

z軸周りの制御回転 (exp(iθz/2)) GateCall (GateCall2) を生成し、ターゲット `q_target` に適用される制御はインデックス `q_ctrl` に基づきます。

# 例

```julia-repl
julia> QXZoo.DefaultGates.c_r_z( 0, 1, pi/4)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbolP(:c_r_z, 0, false, 0.7853981633974483), 0, 1, nothing)
```
