```julia
recursivecopy(a::Union{AbstractArray{T, N}, AbstractVectorOfArray{T, N}})
```

再帰的な `copy` 関数。配列の配列に対しては `deepcopy` のように動作しますが、スカラーの配列に対しては `copy` のように動作します。
