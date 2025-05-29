```
hmesh(P::AbstractArray{Float64,2}, F::Vector{Vector{Int64}},N::Matrix{Float64}; args...)
```

  * P 点の行列
  * F 面の配列
  * N (オプション) 法線の行列

点の配列と面の配列からHMeshを構築します。
