```
c_y(q_target::Int, q_ctrl::Int)
```

制御されたパウリ-y（2量子ビット）ゲートコール（GateCall2）を生成します。これは、ターゲット `q_target` に適用される `q_ctrl` インデックスで制御されます。

# 例

```julia-repl
julia> QXZoo.DefaultGates.c_y(0, 1)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbol(:c_y, 0, false), 0, 1, QXZoo.GateOps.GateSymbol(:y, 0, false))
```
