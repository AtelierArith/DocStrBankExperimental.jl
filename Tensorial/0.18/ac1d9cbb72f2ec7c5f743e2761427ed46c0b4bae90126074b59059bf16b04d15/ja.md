```
minorsymmetric(::AbstractFourthOrderTensor) -> SymmetricFourthOrderTensor
```

4次元テンソルのマイナー対称部分を計算します。

# 例

```jldoctest
julia> x = rand(Tensor{Tuple{3,3,3,3}});

julia> minorsymmetric(x) ≈ @einsum (i,j,k,l) -> (x[i,j,k,l] + x[j,i,k,l] + x[i,j,l,k] + x[j,i,l,k]) / 4
true
```
