`Brieskorn_normal_form(b::LocallyGarsideElt)`

Brieskorn  citeBri71 has noticed that if `L(b)`  is the left descent set of `b`  (see [`leftdescents`](@ref)),  and if  `b_(L(b))` is  the right lcm of `L(b)`,  then  `b_(L(b))`  left-divides  `b`.  We  can  now  divide  `b` by `b_(L(b))`  and continue  this process  with the  quotient. In this way, we obtain  an expression  `b=b_(L₁)⋯ b_(Lᵣ)`  where `Lᵢ=L(b_(Lᵢ)⋯ b_(Lᵣ))` for all  `i`, which we  call the *Brieskorn  normal form* of  `b`. The function `Brieskorn_normal_form`  returns a  description of  this form, by returning the   list  of  sets   `L(b)`  which  describe   the  above  decomposition.

```julia-repl
julia> W=coxgroup(:E,8);B=BraidMonoid(W)
BraidMonoid(E₈)

julia> w=B(2,3,4,2,3,4,5,4,2,3,4,5,6,5,4,2,3,4,5,6,7,6,5,4,2,3,4,5,6,7,8)
2342345423456542345676542345678

julia> Brieskorn_normal_form(w)
2-element Vector{Vector{Int64}}:
 [2, 3, 4, 5, 6, 7]
 [8]

julia> Brieskorn_normal_form(w^2)
2-element Vector{Vector{Int64}}:
 [2, 3, 4, 5, 6, 7, 8]
 [2, 3, 4, 5, 6]
```
