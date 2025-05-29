`UnipotentGroup(W;chevalley=nothing,order=1:nref(W))`

`W` はウィール群である必要があります。この関数は、ウィール群 `W` に関連付けられた `struct UnipotentGroup` を返します。

キーワード `order` が指定されている場合、それは正の根に対する全順序であり、非可換要素を正規化するために使用されます。

デフォルトでは、構造定数 `Nᵣₛ` は、extraspecial ペアからの [Carter1972](biblio.htm#Car72b) の方法を使用して計算されます。別の構造定数のセットは、キーワード `chevalley` に対して、根インデックスのペア `(r,s)` にいくつかのオブジェクト `p` を関連付ける `Dict` を指定することによって指定できます。ここでは、Meinolf Geck のパッケージ `ChevLie` から異なる定数を使用する例を示します。

```julia-rep1
julia> W=coxgroup(:G,2)
G₂

julia> using ChevLie: LieAlg, structconsts

julia> l=LieAlg(:g,2)
#I dim = 14
LieAlg('G2')

julia> U=UnipotentGroup(W;chevalley=structconsts(l))
#I calculating structconsts
#I calculating eps-canonical base (100/.) 
UnipotentGroup(G₂)
```
