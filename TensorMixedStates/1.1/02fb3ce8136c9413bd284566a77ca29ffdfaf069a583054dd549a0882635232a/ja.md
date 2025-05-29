```
type Operator{T, N} <: ExprOp{T, N}
```

基本演算子の型（`X`、`Swap`、`C` など）、`T` は `Pure` または `Mixed` で、`N` は Int です。

# 例

```
Operator("X")                      サイトによって事前に定義された値を持つ基本演算子
Operator("Z", [1 0 ; 0 -1])
Operator{Pure, 2}("Swap", [ 1 0 0 0 ; 0 0 1 0 ; 0 1 0 0 ; 0 0 0 1])
Operator("CX", controlled(X))
Operator("Sx", (Sp + Sm) / 2)
Operator("C", [0 1 ; 0 0], true)   フェルミオン演算子
```
