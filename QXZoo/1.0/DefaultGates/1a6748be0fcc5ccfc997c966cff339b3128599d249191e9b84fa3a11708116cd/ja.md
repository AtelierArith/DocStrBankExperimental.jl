```
c_u(label::GateSymbol, q_target::Int, q_ctrl::Int)
```

制御ユニタリ（2量子ビット）ゲートコール（GateCall2）を生成します。これは、ターゲット `q_target` に適用される `q_ctrl` のインデックスで制御されます。

# 例

```julia-repl
julia> QXZoo.DefaultGates.c_u(QXZoo.GateOps.GateSymbol(:myCU), 0, 1)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbol(:myCU, 0, false), 0, 1, nothing)
```
