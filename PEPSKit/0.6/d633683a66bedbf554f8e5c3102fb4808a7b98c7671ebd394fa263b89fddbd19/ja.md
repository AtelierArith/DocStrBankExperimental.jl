```
CTMRGEnv(
    [f=randn, T=ComplexF64], D_north::P, D_east::P, chi_north::S, [chi_east::S], [chi_south::S], [chi_west::S];
    unitcell::Tuple{Int,Int}=(1, 1),
) where {P<:ProductSpaceLike,S<:ElementarySpaceLike}
```

対応する [`InfiniteSquareNetwork`](@ref) の北と東の仮想空間、および環境の北、東、南、西の仮想空間を指定することによって CTMRG 環境を構築します。ネットワークの単位セルは、`unitcell` キーワード引数によって指定できます。デフォルトでは、すべての方向の仮想環境空間は同じものと見なされます。

各サイトの環境仮想空間は、各方向の対応するエッジテンソルの仮想空間に対応しています。
