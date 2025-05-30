```
spectralradius(N::SpeciesInteractionNetwork{<:Unipartite, <:Binary}; correction=:links)
```

ユニパーティットのスペクトル半径は、ネステッドネスの概念的な同等物です [Staniczenko2013ghost](@cite)。これは、*無向*隣接行列の固有値の中で最大の実部の絶対値として定義されます。

`correction`キーワードを通じて利用可能な修正がいくつかあります。

デフォルトの修正は`：links`であり、これは[Staniczenko2013ghost](@citet)において、値がリンクの数の平方根で割られ、*自己相互作用を除外*します。

`:connectance`修正を使用すると、[Phillips2011structure](@citet)のバージョンに従い、値が$(L\times(S-1))S^{-1}$の平方根で割られます（これは*正確には*コネクタンスではありませんが、このバージョンはネットワークのサイズと順序に対して修正されています）。

`:none`を使用すると、生の値が返され、ネットワーク間の比較のためには使用しないことが推奨されます。同じ数の種と相互作用を持つネットワークを比較する場合には適切であり、他の修正よりもわずかに速いため、含まれています。

###### 参考文献

[Phillips2011structure](@citet*)

[Staniczenko2013ghost](@citet*)
