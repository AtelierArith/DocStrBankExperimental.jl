```
ispolynomial(s::AbstractSystem)
```

システム `s` の動力学が多項式方程式によって指定されているかどうかを判断します。

この関数の結果はシステムのタイプのみに依存し、値には依存しないため、`typeof(s)` にも適用できます。したがって、例えば `LinearContinuousSystem` は多項式タイプとは見なされません。
