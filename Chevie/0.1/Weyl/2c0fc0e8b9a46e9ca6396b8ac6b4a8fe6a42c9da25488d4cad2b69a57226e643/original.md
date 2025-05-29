`coxeter_group(type,rank[,bond];sc=false)` (or `coxgroup`)

If `C=cartan(type,rank[,bond])`, this is equivalent to `rootdatum(C)`. If `sc=true` this is equivalent to `rootdatum(permutedims(C),one(C))`.

The  resulting object `W`, a  `FiniteCoxeterGroup`, has an additional entry compared to a `PermRootGroup`.

  * `W.rootdec`:  the root vectors, given  as linear combinations of simple roots.  The first `nref(W)` roots are  positive, the next `nref(W)` are the corresponding negative roots. Moreover, the first `semisimplerank(W)`  roots are the simple roots. The positive roots are ordered by increasing height.

and `roots(W)` is ordered is the same way as `W.rootdec`.

For  how to  get various  information on  the root  system and  the Coxeter group,   see  the  functions   `nref,  coroots,  rootlengths,  simple_reps, simple_conjugating,  reflrep,  simpleroots,  simplecoroots,  PermX, cartan, inclusion, restriction, action, rank, semisimplerank`

In terms of root data, this function returns the adjoint root datum of Weyl group  `W`.  If  `sc=true`  it  returns  the  simply  connected root datum.

```julia_repl
julia> W=coxgroup(:G,2)
G₂

julia> cartan(W)
2×2 Matrix{Int64}:
  2  -1
 -3   2

julia> W.rootdec
12-element Vector{Vector{Int64}}:
 [1, 0]
 [0, 1]
 [1, 1]
 [1, 2]
 [1, 3]
 [2, 3]
 [-1, 0]
 [0, -1]
 [-1, -1]
 [-1, -2]
 [-1, -3]
 [-2, -3]

julia> reflrep(W)
2-element Vector{Matrix{Int64}}:
 [-1 0; 1 1]
 [1 3; 0 -1]
```
