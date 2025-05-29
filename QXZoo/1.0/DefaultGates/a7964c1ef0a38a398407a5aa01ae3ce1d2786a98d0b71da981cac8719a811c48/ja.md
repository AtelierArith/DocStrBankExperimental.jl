```
c_r_phase(q_target::Int, q_ctrl::Int, theta::Real)
```

制御された位相回転を生成します（制御された [1 0; 0 exp(iθ)] GateCall (GateCall2)）、インデックス `q_ctrl` に基づいてターゲット `q_target` に適用されます。

# 例

```julia-repl
julia> QXZoo.DefaultGates.c_r_phase( 0, 1, pi/7 )
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbolP(:c_r_phase, 0, false, 0.4487989505128276), 0, 1, nothing)
```
