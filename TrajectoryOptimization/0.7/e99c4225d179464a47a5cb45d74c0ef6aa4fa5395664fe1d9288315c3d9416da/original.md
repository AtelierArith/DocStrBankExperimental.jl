```
LQRObjective(Q, R, Qf, xf, N)
```

Create an objective of the form $(x_N - x_f)^T Q_f (x_N - x_f) + \sum_{k=0}^{N-1} (x_k-x_f)^T Q (x_k-x_f) + u_k^T R u_k$

Where `eltype(obj) <: DiagonalCost` if `Q`, `R`, and `Qf` are     `Union{Diagonal{<:Any,<:StaticVector}}, <:StaticVector}`
