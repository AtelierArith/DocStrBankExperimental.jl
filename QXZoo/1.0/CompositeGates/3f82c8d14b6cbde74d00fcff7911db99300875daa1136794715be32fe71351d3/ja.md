```
iswap(q_target1::Int, q_target2::Int)
```

iSWAPゲートの同等回路を生成します。これは、`exp(1im*(pi/4)*(kron(GateMap.x(),GateMap.x()) + kron(GateMap.y(),GateMap.y())))`を使用して生成できます。

# 例

```julia-repl

```
