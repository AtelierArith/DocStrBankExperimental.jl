```
cumulants(X::Matrix, m::Int, b::Int)
```

返す [SymmetricTensor{Float, 1}, SymmetricTensor{Float, 2}, ..., SymmetricTensor{Float, m}]、累積テンソルのベクトル

```
julia> M =  [[-0.88626   0.279571];[-0.704774  0.131896]];

julia> convert(Array, cumulants(M, 3)[3])
2×2×2 Array{Float64,3}:
[:, :, 1] =
 0.0  0.0
 0.0  0.0

[:, :, 2] =
 0.0  0.0
 0.0  0.0
```
