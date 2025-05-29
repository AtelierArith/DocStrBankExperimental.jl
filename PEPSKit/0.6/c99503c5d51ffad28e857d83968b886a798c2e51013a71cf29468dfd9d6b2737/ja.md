```
InfinitePartitionFunction(
    [f=randn, T=ComplexF64,] Pspace::S, Nspace::S, [Espace::S]; unitcell=(1,1)
) where {S<:ElementarySpaceLike}
```

物理的、北および東の空間と単位セルを指定することによって、InfinitePartitionFunctionを作成します。空間は`Int`または`ElementarySpace`を介して指定できます。
