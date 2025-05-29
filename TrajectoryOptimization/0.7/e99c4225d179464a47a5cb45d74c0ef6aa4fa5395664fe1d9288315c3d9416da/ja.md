```
LQRObjective(Q, R, Qf, xf, N)
```

次の形式の目的を作成します：$(x_N - x_f)^T Q_f (x_N - x_f) + \sum_{k=0}^{N-1} (x_k-x_f)^T Q (x_k-x_f) + u_k^T R u_k$

ここで、`eltype(obj) <: DiagonalCost` である場合、`Q`、`R`、および `Qf` は `Union{Diagonal{<:Any,<:StaticVector}}, <:StaticVector}` です。
