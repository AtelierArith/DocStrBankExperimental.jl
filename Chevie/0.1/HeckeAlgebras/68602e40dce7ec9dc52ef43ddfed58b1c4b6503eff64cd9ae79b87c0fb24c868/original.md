`char_values(h::HeckeTElt)`

`h` is an element of an Iwahori-Hecke algebra `H`. The function returns the values  of the irreducible characters of `H`  on `h` (the method used is to convert to the `T` basis, and then use `class_polynomials`).

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> H=hecke(W,q^2;rootpara=q)
hecke(B₂,q²,rootpara=q)

julia> char_values(Cpbasis(H)(1,2,1))
5-element Vector{Pol{Int64}}:
 -q-q⁻¹
 q+q⁻¹
 0
 q³+2q+2q⁻¹+q⁻³
 0
```
