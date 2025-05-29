`central_monomials(H)`

Let  `H`  be  an  Hecke  algebra  for  the finite reflection group `W`. The function  returns the scalars by which the image  in `H` of `π` acts on the irreducible representations of `H`.

When  `W` is irreducible,  `π` is the  generator of the  center of the pure braid  group.  In  general,  it  is  the  product of such elements for each irreducible  component. When  `W` is  a Coxeter  group, the  image of  π in `H` is $T_{w_0}^2$.

```julia-repl
julia> H=hecke(coxgroup(:H,3),Pol(:q))
hecke(H₃,q)

julia> central_monomials(H)
10-element Vector{Pol{Cyc{Int64}}}:
 1
 q³⁰
 q¹²
 q¹⁸
 q¹⁰
 q¹⁰
 q²⁰
 q²⁰
 q¹⁵
 q¹⁵
```
