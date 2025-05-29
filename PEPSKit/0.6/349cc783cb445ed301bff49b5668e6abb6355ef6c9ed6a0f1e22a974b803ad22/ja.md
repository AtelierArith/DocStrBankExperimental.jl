```
CTMRGEnv(
    [f=randn, T=ComplexF64], network::InfiniteSquareNetwork, chis_north::A, [chis_east::A], [chis_south::A], [chis_west::A]
) where {A<:AbstractMatrix{<:ElementarySpaceLike}}}
```

対応する [`InfiniteSquareNetwork`](@ref) を指定し、環境の北、東、南、西の仮想空間を行列として構築することで CTMRG 環境を構成します。それぞれの行列のエントリは単位セル内のサイトに対応します。デフォルトでは、すべての方向の仮想空間は同じものと見なされます。

各サイトの環境仮想空間は、各方向の対応するエッジテンソルの北または東の仮想空間に対応します。具体的には、与えられたサイト `(r, c)` に対して、`chis_north[r, c]` は北エッジテンソルの東空間に対応し、`chis_east[r, c]` は東エッジテンソルの北空間に対応し、`chis_south[r, c]` は南エッジテンソルの東空間に対応し、`chis_west[r, c]` は西エッジテンソルの北空間に対応します。
