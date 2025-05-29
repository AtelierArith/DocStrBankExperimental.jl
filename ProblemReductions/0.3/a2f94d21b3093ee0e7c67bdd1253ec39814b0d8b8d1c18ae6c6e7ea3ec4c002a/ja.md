```julia
struct Matching{T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

[Vertex matching](https://queracomputing.github.io/GenericTensorNetworks.jl/dev/generated/Matching/) 問題。

## 位置引数

  * `graph` は問題のグラフです。
  * `weights` は `graph` の辺に関連付けられています。
