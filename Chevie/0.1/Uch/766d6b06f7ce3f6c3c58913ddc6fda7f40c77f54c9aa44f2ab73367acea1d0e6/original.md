`cuspidal(uc::UnipotentCharacters[,e])`

A  unipotent character `γ` of a  finite reductive group `𝐆` is `e`-cuspidal if  its  Lusztig  restriction  to  any  proper `e`-split Levi is zero. When `e==1`  (the default when  `e` is omitted)  we recover the  usual notion of cuspidal character. Equivalently the `Φₑ`-part of the generic degree of `γ` is equal to the `Φₑ`-part of the generic order of the adjoint group of `𝐆`. This  makes  sense  for  any  Spetsial  complex  reflection  group  and  is implemented for them.

The  function returns the list of indices of unipotent characters which are `e`-cuspidal.

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> cuspidal(UnipotentCharacters(W))
1-element Vector{Int64}:
 14

julia> cuspidal(UnipotentCharacters(W),6)
8-element Vector{Int64}:
  1
  2
  6
  7
  8
  9
 10
 12

julia> cuspidal(UnipotentCharacters(complex_reflection_group(4)),3)
4-element Vector{Int64}:
  3
  6
  7
 10
```
