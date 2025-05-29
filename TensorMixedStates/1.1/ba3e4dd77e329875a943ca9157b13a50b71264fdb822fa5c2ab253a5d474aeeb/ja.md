```
abstract type ExprOp{T, N}
```

演算子の抽象型であり、`T` は `Pure` または `Mixed` で、`N` は一般的な演算子のための `Int` です（演算子が適用される可能性のあるサイトの数）およびインデックス付き演算子のための `IndexOp` です。

```
SimpleOp = ExprOp{Pure, 1}
ExprIndexed{T} = ExprOp{T, IndexOp}
```
