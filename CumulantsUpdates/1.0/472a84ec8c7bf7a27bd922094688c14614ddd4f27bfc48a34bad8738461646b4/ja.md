moms2cums!(M::Vector{SymmetricTensor})

モーメントの対称テンソルのベクトルを累積量の対称テンソルのベクトルに変換します。

```jldocstests

julia> m = momentarray(ones(20,3), 3);

julia> moms2cums!(m)

julia> m[3]

SymmetricTensors.SymmetricTensor{Float64,3}(Union{Array{Float64,3}, Void}[[0.0 0.0; 0.0 0.0]
[0.0 0.0; 0.0 0.0] #undef; #undef #undef]
```
