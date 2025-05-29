```
x(q_target::Int)
```

ターゲットキュービットに適用される単一キュービットパウリ-xゲートコール（GateCall1）を生成します。

# 例

```julia-repl
julia> QXZoo.DefaultGates.x(0)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbol(:x, 0, false), 0)
```
