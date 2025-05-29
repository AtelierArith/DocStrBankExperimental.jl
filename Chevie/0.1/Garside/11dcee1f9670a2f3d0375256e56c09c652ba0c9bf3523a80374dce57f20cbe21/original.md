`conjcat(b[,F];ss=Val(:sc))`

returns  the conjugacy category  of the summit  set of `b`  of the required type.

  * By default,  computes the  category of  sliding circuits  of `b`.
  * If `ss==Val(:ss)`,  computes  the  super  summit  set.
  * If `ss==Val(:cyc)`, computes the cyclic  conjugacy category.
  * If `ss==Val(:inf)` computes the category of all conjugate elements with same `Inf` as `b`.

If  an argument  `F` is  given it  should be  the Frobenius of a Reflection coset attached to `b.M.W`. Then the `F`-conjugacy category is returned.

```julia-repl
julia> W=coxgroup(:A,4)
A₄

julia> w=BraidMonoid(W)(4,3,3,2,1)
43.321

julia> C=conjcat(w)
category with 2 objects and 4 generating maps

julia> C.obj # the (sliding circuits) summit set
2-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 32143
 21324
```

```julia-rep1
julia> xprint(C;graph=true)   # show the conjugations among the summit set
category with 2 objects and 4 generating maps
     32143      21343      21324      13214
32143────→ 32143────→ 21324────→ 21324────→ 32143
```

```julia-repl
julia> conjcat(w;ss=Val(:ss)).obj # the super summit set
4-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 32143
 13243
 21432
 21324
```
