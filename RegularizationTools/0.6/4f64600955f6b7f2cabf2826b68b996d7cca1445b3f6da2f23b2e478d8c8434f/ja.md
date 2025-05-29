```
setupRegularizationProblem(A::AbstractMatrix, L::AbstractMatrix)
```

設計行列とティホノフ平滑化行列に基づいて正則化問題を初期化するための行列を事前計算します。Hansen (1998, Eq. 2.35) を参照してください。

使用例

```julia
Ψ = setupRegularizationProblem(A, L) 
```
