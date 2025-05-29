`relative_degrees(WF,ζ::Root1=1)`

Let  `WF` be a reflection group or a  reflection coset and `ζ` be a root of unity.  Then if $V_ζ$ is the `ζ`-eigenspace  of some element of `WF`, and is of maximal dimension among such `ζ`-eigenspaces (and if `WF` is a coset `W`  is the group of `WF`) then $N_W(V_ζ)/C_W(V_ζ)$ is a reflection group in  its  action  on  $V_ζ$.  The  function `relative_degrees` returns the reflection  degrees of this complex reflection group, which are a subset of those of `W`. These degrees are computed by an invariant-theoretic formula: if   `(d₁,ε₁),…,(dₙ,εₙ)`  are   the  generalized   degrees  of   `WF`  (see [`degrees`](@ref)) they are the `dᵢ` such that `ζ^{dᵢ}=εᵢ`.

The  eigenvalue `ζ` can also  be specified by giving  an integer `d` (which then  specifies  `ζ=E(d)`)  or  a  fraction  `a//b`  which  then  specifies `ζ=E(b,a)`. If omitted, `ζ` is taken to be `1`.

```julia-repl
julia> W=coxgroup(:E,8)
E₈

julia> relative_degrees(W,4) # the degrees of G₃₂
4-element Vector{Int64}:
  8
 12
 20
 24
```
