`Reflection` is a `struct` representing a reflection in a reflection group.

```julia-repl
julia> W=crg(8);

julia> r=reflections(W)[7] # shows (r.W,r.rootno,r.eigen)
Reflection(G₈,1,-1)

julia> r.rootno # r is a reflection for the first root
1

julia> r.eigen # the non-trival eigenvalue, as a Root1
Root1: -1

julia> r.W # the group of which r is a reflection
G₈

julia> r==Reflection(W,1,-1) # specify r with .rootno and .eigen
true

julia> Reflection(W,1) # specify with .rootno gets the distinguished reflection
Reflection(G₈,1,ζ₄)

julia> root(r)
2-element Vector{Cyc{Rational{Int64}}}:
  0
 ζ₄

julia> coroot(r)
2-element Vector{Cyc{Int64}}:
    0
 -2ζ₄

julia> Matrix(r)
2×2 Matrix{Cyc{Rational{Int64}}}:
 1   0
 0  -1

julia> hyperplane(r) # the fixed hyperplane, as a rowspace
1×2 Matrix{Cyc{Rational{Int64}}}:
 1  0

julia> hyperplane(r)*Matrix(r)==hyperplane(r)
true

julia> isdistinguished(r) # r is not distinguished
false

julia> exponent(r) # which power of a distinguished reflection it is
2

julia> Perm(r)
(1,8)(2,9)(3,16)(4,15)(5,17)(6,18)(7,19)(10,22)(11,21)(12,23)

julia> hyperplane_orbit(r) # r is in the first hyperplane orbit
1

julia> position_class(r) # the index of the conjugacy class of r in W 
15

julia> simple_rep(r) # smallest root index affording a conjugate reflection
1

julia> word(r) # a word in the generators of r.W for r
2-element Vector{Int64}:
 1
 1
```
