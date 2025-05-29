`invariants(W::ComplexReflectionGroup)`

returns  the fundamental invariants of `W` in its reflection representation `V`.  That is, returns  a set of  algebraically independent elements of the symmetric  algebra  of  the  dual  of  `V` which generate the `W`-invariant polynomial  functions on `V`. Each such invariant function is returned as a function:  if `e₁,…,eₙ` is a basis of `V` and `f` is the function, then the value  of the polynomial  function on `a₁e₁+…+aₙeₙ`  is obtained by calling `f(a₁,…,aₙ)`. This function depends on the classification, and is dependent on the exact reflection representation of `W`. So for the moment it is only implemented   when  the  reflection   representation  for  the  irreducible components has the same Cartan matrix as the one provided by Chevie for the corresponding  irreducible  group.  The  polynomials  are invariant for the natural   action  of   the  group   elements  as   matrices;  that  is,  if `m==reflrep(W,w)`  for some  `w` in  `W`, then  an invariant  `f` satisfies `f(a₁,…,aₙ)=f(v₁,…,vₙ)`   where  `[v₁,…,vₙ]=[a₁,…,aₙ]×m`.  This  action  is implemented on `Mvp`s by the function `^`.

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> @Mvp x,y,z

julia> i=invariants(W);

julia> map(f->f(x,y),i)
2-element Vector{Mvp{Int64, Int64}}:
 -2x²+2xy-2y²
 6x²y-6xy²

julia> W=complex_reflection_group(24)
G₂₄

julia> p=invariants(W)[1](x,y,z)
Mvp{Rational{Int64}}: (14//1)x⁴+(-12//1)x²y²+(-42//1)x²yz+(21//2)x²z²+(18//7)y⁴+(-6//1)y³z+(-9//2)y²z²+(-21//8)z⁴

julia> map(v->^(v,reflrep(W,1);vars=[:x,:y,:z]),(x,y,z))
((1//2)x+(3√-7/14)y, (-√-7/2)x+(-1//2)y, z)

julia> p^reflrep(W,1)-p
Mvp{Cyc{Rational{Int64}}}: 0
```
