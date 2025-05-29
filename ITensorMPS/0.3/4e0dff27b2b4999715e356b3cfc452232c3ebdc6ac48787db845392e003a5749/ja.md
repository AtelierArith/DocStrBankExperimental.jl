```
orthogonalize!(M::MPS, j::Int; kwargs...)
orthogonalize(M::MPS, j::Int; kwargs...)

orthogonalize!(M::MPO, j::Int; kwargs...)
orthogonalize(M::MPO, j::Int; kwargs...)
```

MPSの直交性中心をサイト`j`に移動します。MPSの観測可能な特性は変更されず、ボンドインデックスの切り捨ても行われません。その後、テンソル`1,2,...,j-1`は左直交し、テンソル`j+1,j+2,...,N`は右直交します。

`orthogonalize!`を使用してインプレースで修正するか、`orthogonalize`を使用してアウトオブプレースで修正します。
