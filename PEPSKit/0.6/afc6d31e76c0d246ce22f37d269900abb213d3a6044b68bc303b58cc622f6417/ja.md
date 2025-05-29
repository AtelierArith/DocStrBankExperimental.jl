```
CTMRGEnv(
    [f=randn, T=ComplexF64,] network::InfiniteSquareNetwork, chi_north::S, [chi_east::S], [chi_south::S], [chi_west::S],
) where {S<:ElementarySpaceLike}
```

対応する [`InfiniteSquareNetwork`](@ref) を指定し、環境の北、東、南、西の仮想空間を指定することで CTMRG 環境を構築します。デフォルトでは、すべての方向の仮想空間は同じものと見なされます。

各サイトの環境仮想空間は、各方向の対応するエッジテンソルの仮想空間に対応します。
