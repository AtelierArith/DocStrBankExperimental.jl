```
u(label::String, q_target::Int)
```

ターゲットキュービットに適用される単一キュービット任意ユニタリゲートコール (GateCall1) を生成します。

# 例

```julia-repl
julia> QXZoo.DefaultGates.u("mygate", 1)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbol(:mygate, 0, false), 0)
```
