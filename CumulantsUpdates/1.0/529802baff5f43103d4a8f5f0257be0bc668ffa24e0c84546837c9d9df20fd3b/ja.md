```
momentupdat(M::SymmetricTensor{Float, N}, X::Matrix, Xplus::Matrix)
```

元のモーメント、元のデータ、およびデータの更新 - dataup を考慮して更新された SymmetricTensor{Float, N} を返します。

```jldocstests
julia> x = ones(6, 2);

julia> m = moment(x, 3);

julia> y = 2*ones(2,2);

julia> momentupdat(m, x, y)
SymmetricTensors.SymmetricTensor{Float64,3}(Union{Array{Float64,3}, Void}[[3.33333 3.33333; 3.33333 3.33333]
[3.33333 3.33333; 3.33333 3.33333]], 2, 1, 2, true)

```
