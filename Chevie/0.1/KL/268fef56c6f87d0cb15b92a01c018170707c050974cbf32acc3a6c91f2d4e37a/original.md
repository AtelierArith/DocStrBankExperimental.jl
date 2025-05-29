`KLPol(W,y,w)` returns the Kazhdan-Lusztig polynomial `P_{y,w}` of `W`.

To  compute Kazhdan-Lusztig polynomials in  the one-parameter case it still seems   best  to   use  the   recursion  formula   in  the  original  paper [KL79](biblio.htm#KL79).  We first perform  a series of  checks on the pair `(y,w)`  to see if  the computation of  the corresponding polynomial can be reduced  to  a  similar  calculation  for  elements  of  smaller length. In particular, we reduce to the case of critical pairs (see [`KL.critical_pair`](@ref)),  and whenever the  polynomial corresponding to such  a pair is computed, the value is  stored in a `Dict` `W.klpol` in the underlying Coxeter group.

```julia-repl
julia> W=coxgroup(:B,3)
B₃

julia> map(i->map(x->KLPol(W,one(W),x),elements(W,i)),1:nref(W))
9-element Vector{Vector{Pol{Int64}}}:
 [1, 1, 1]
 [1, 1, 1, 1, 1]
 [1, 1, 1, 1, 1, 1, 1]
 [1, 1, 1, 1, 1, x+1, 1, 1]
 [x+1, 1, x+1, x+1, 1, 1, x+1, 1]
 [x²+1, 1, x+1, x+1, x+1, 1, 1]
 [1, 1, x²+x+1, x+1, x+1]
 [1, x+1, x²+1]
 [1]
```

Our code is based on Meinolf Geck's code for GAP3/Chevie.
