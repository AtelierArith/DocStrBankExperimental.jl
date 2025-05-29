`word(b::GarsideElt)`

returns  a description  of `b`  as a  list of  the atoms  of which  it is a product.  If `b` is in the Garside group  but not the Garside monoid, it is represented  in  fraction  normal  form  where  as a special convention the inverses  of  the  atoms  are  represented  by  negating  the corresponding integer.

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> b=B(2,1,2,1,1)*inv(B(2,2))
(21)⁻¹1.12.21

julia> word(b)
7-element Vector{Int64}:
 -1
 -2
  1
  1
  2
  2
  1
```
