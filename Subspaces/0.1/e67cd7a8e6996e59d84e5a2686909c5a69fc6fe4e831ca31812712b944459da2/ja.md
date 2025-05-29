```julia
dim(S::Subspaces.Subspace) -> Int64

```

この部分空間の線形次元を返します。

```jldoctest
julia> dim(Subspace([ [1,2,3], [4,5,6] ]))
2
```
