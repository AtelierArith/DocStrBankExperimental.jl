```
VectorSolution
```

要素の型 `T` によってエンコードされた抽象的な解決策。

具体的なサブタイプは以下を実装する必要があります：

  * スーパタイプ `Solution` のすべての要件
  * `x::AbstractVector`: 解を表すベクトル
  * `destroyed::Union{Nothing, Int[]}`: 破壊された要素の位置のベクトル、例えば LNS で destroy+repair 演算子を使用する際
