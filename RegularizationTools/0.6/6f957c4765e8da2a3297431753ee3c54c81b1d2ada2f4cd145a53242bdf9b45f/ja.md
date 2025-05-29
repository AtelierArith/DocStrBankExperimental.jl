```
setupRegularizationProblem(A::AbstractMatrix, order::Int)
```

設計行列 A とゼロ次、一次、または二次差分演算子に基づいて正則化問題を初期化するための行列を事前計算します。詳細については、Hanson (1998) およびソースコードを参照してください。

使用例

```julia
Ψ = setupRegularizationProblem(A, 0) # ゼロ次の問題
Ψ = setupRegularizationProblem(A, 2) # 二次の問題
```
