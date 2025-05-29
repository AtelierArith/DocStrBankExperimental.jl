```
z(q_target::Int)
```

ターゲットキュービットに適用される単一キュービットパウリ-zゲートコール（GateCall1）を生成します。

# 例

```julia-repl
julia> QXZoo.DefaultGates.z(0)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbol(:z, 0, false), 0)
```
