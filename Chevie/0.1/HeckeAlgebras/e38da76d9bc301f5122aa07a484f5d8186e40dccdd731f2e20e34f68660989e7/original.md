`hecke( W [, parameter];rootpara=nothing)`

Hecke  algebra for the complex reflection group or Coxeter group `W`. If no `parameter` is given, `1` is assumed which gives the group algebra of `W`.

The  following forms are accepted for  `parameter`: if `parameter` is not a vector or a tuple, it is replaced by the vector `fill(parameter,ngens(W))`. If it is a vector with one entry, it is replaced with `fill(parameter[1],ngens(W))`.  If `parameter`  is a  vector with more than one  entry, it should  have length `ngens(W)`,  each entry representing the parameters   for   the   corresponding   generator   of  `W`,  and  entries corresponding  to  the  same  `W`-orbit  of generators should be identical. Finally, if `parameter` is a `Tuple`, the tuple should have as many entries as  there are hyperplane  orbits in `W`  and each entry  will represent the parameters for the corresponding conjugacy class of braid reflections.

An  entry in  `parameter` for  a reflection  of order  `e` can  be either a single scalar value or a `Vector` of length 'e'. If it is a `Vector`, it is interpreted as the list `[u₀,…,u_(e-1)]` of parameters for that reflection. If  it is not  a vector, let  `q` be its  value; it is  then interpreted as specifying  the  list  of  parameters  for  the Spetsial algebra, which are `[q,ζ_e,…,ζ_{e-1}]`  (thus the  list `[q,-1]`  of the one-parameter algebra for Coxeter groups).

When  printing an Hecke algebra the parameter list is abbreviated using the same conventions.

Computing characters or representations of Hecke algebra needs sometimes to extract  roots of the  parameters. These roots  are extracted automatically (when  possible). For Coxeter groups it  is possible to give explicit roots by  giving  a  keyword  argument  `rootpara`:  if  it is a vector it should contain at the `i`-th position a square root of `-parameter[i][1]*parameter[i][2]`;   if  a   scalar  it   is  replaced  by `fill(rootpara,ngens(W))`.

# Example

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> @Pol q
Pol{Int64}: q

julia> H=hecke(W,q)
hecke(B₂,q)

julia> H.para
2-element Vector{Vector{Pol{Int64}}}:
 [q, -1]
 [q, -1]

julia> H=hecke(W,q^2,rootpara=-q)
hecke(B₂,q²,rootpara=-q)

julia> H=hecke(W,q^2)
hecke(B₂,q²)

julia> rootpara(H)
2-element Vector{Pol{Int64}}:
 q
 q

julia> H
hecke(B₂,q²,rootpara=q)

julia> H=hecke(W,[q^2,q^4],rootpara=[q,q^2])
hecke(B₂,Pol{Int64}[q², q⁴],rootpara=Pol{Int64}[q, q²])

julia> H.para,rootpara(H)
(Vector{Pol{Int64}}[[q², -1], [q⁴, -1]], Pol{Int64}[q, q²])

julia> H=hecke(W,9,rootpara=3)
hecke(B₂,9,rootpara=3)

julia> H.para,rootpara(H)
([[9, -1], [9, -1]], [3, 3])

julia> @Mvp x,y,z,t

julia> H=hecke(W,[[x,y]])
hecke(B₂,Vector{Mvp{Int64, Int64}}[[x, y]])

julia> rootpara(H);H
hecke(B₂,Vector{Mvp{Int64, Int64}}[[x, y]],rootpara=ζ₄x½y½)

julia> H=hecke(W,[[x,y],[z,t]])
hecke(B₂,Vector{Mvp{Int64, Int64}}[[x, y], [z, t]])

julia> rootpara(H);H
hecke(B₂,Vector{Mvp{Int64, Int64}}[[x, y], [z, t]],rootpara=Mvp{Cyc{Int64}, Rational{Int64}}[ζ₄x½y½, ζ₄t½z½])

julia> hecke(coxgroup(:F,4),(q,q^2)).para
4-element Vector{Vector{Pol{Int64}}}:
 [q, -1]
 [q, -1]
 [q², -1]
 [q², -1]

julia> hecke(complex_reflection_group(3,1,2),q).para # spetsial parameters
2-element Vector{Vector{Pol{Cyc{Int64}}}}:
 [q, ζ₃, ζ₃²]
 [q, -1]
```
