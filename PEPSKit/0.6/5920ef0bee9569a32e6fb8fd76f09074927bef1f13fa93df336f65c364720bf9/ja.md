```
InfinitePartitionFunction(
    [f=randn, T=ComplexF64,] Pspaces::A, Nspaces::A, [Espaces::A]
) where {A<:AbstractMatrix{<:Union{Int,ElementarySpace}}}
```

ユニットセル内の各サイトにおけるPEPSテンソルの物理、北の仮想、および東の仮想空間を行列として指定することによって`InfinitePartitionFunction`を作成します。各個別の空間は`Int`または`ElementarySpace`のいずれかとして指定できます。
