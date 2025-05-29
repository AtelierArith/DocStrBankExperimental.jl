`WGraphToRepresentation(coxrank::Integer,graph,v)`

We  store some  representations of  one-parameter Iwahori-Hecke algebras as `W`-graphs.  For a Coxeter system `(W,S)`, a  `W`-graph is defined by a set of  vertices `C`  with a  function `I`  which attaches  to `x∈  C` a subset `I(x)⊂ S`, and *edge labels* which to `(x,y)∈ C^2` attach `μ(x,y)∈ K` where `K` is the field of definition of `W`; this defines a representation of the Hecke  algebra  with  parameters  `v`  and  `-v⁻¹`  on  a  space with basis ${e_y}_{y∈ C}$ by:

$Tₛ(e_y)=-e_y$ if `s∈ I(y)` and otherwise $Tₛ(e_y)=v^2 e_y+∑_{x∣s∈ I(x)} vμ(x,y)eₓ$.

The  `W`-graphs are  stored in  a compact  format to  save space.  They are represented as a pair.

  * The  first element is a list describing `C`. Its  elements are either a vector   `I(x)`  of  indices  in  `eachindex(S)`,  or  an  integer  `n` specifying to repeat the previous element `n` more times.
  * The  second element is a list which  specifies `μ`.

We   first   describe   the   `μ`-list   for   symmetric  `W`-graphs  (when `μ(x,y)=μ(y,x)`).  There is one  element of the  `μ`-list for each non-zero value `m` taken by `μ`, which consists of a pair whose first element is `m` and  whose second element is a list of  lists; if `l` is one of these lists each  pair `[l[1],l[i]]`  represents an  edge (`x=l[1]`,`y=l[i]`) such that `μ(x,y)=μ(y,x)=m`.  For non-symmetric `W`-graphs, the first element of each pair  in the `μ`-list  is a pair  `[m1,m2]` and each  edge `[x,y]` obtained from  the lists in the second element  has to be interpreted as `μ(x,y)=m1` and `μ(y,x)=m2`.

```julia-repl
julia> W=coxgroup(:H,3)
H₃

julia> g=Wgraph(W,3)
2-element Vector{Vector{Vector{Any}}}:
 [[2], [1, 2], [1, 3], [1, 3], [2, 3]]
 [[-1, [[1, 3], [2, 4], [3, 5], [4, 5]]]]

julia> WGraphToRepresentation(3,g,Pol(:x))
3-element Vector{Matrix{Pol{Int64}}}:
 [x² 0 … 0 0; 0 -1 … 0 0; … ; 0 0 … -1 -x; 0 0 … 0 x²]
 [-1 0 … 0 0; 0 -1 … -x 0; … ; 0 0 … x² 0; 0 0 … -x -1]
 [x² 0 … 0 0; 0 x² … 0 0; … ; 0 -x … -1 0; 0 0 … 0 -1]
```
