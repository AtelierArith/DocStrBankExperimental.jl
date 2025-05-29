```
y(q_target::Int)
```

ターゲットキュービットに適用される単一キュービットパウリ-yゲートコール（GateCall1）を生成します。

# 例

```julia-repl
julia> QXZoo.DefaultGates.y(0)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbol(:y, 0, false), 0)
```
