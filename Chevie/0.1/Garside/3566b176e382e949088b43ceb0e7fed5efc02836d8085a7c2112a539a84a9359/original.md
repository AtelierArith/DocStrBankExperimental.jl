`image(b::GarsideElt)`

This  function is defined only if `b`  is an element of an interval monoid, for instance a braid. It returns the image of `b` in the group of which the monoid  is an interval  monoid. For instance  it gives the  projection of a braid in an Artin monoid back to the Coxeter group.

```julia-repl
julia> W=coxsym(4)
𝔖 ₄

julia> b=BraidMonoid(W)(2,1,2,1,1)
121.1.1

julia> p=image(b)
(1,3)

julia> word(W,p)
3-element Vector{Int64}:
 1
 2
 1
```
