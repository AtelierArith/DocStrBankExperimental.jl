`UnipotentGroup(W;chevalley=nothing,order=1:nref(W))`

`W` should be a Weyl group. This function returns a `struct UnipotentGroup` associated  to the reductive group of Weyl group `W`. 

If  the keyword `order` is given it is  a total order on the positive roots used to normalize unipotent elements.

By  default the structure constants `Nᵣₛ`  are computed using the method of [Carter1972](biblio.htm#Car72b)  from  extraspecial  pairs.  Another set of structure  constants can be specified by giving for the keyword `chevalley` a `Dict` associating to a pair `(r,s)` of root indices some object `p` such that `first(p)` is the corresponding `N_{r,s}`. Here is an example of using different constants from the package `ChevLie` of Meinolf Geck.

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
