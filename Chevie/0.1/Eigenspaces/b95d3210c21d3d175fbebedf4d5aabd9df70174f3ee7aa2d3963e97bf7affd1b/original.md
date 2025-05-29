`position_regular_class(WF,ζ::Root1=1)`

Let  `WF` be a reflection group or a  reflection coset and `ζ` be a root of unity  such that some element of `WF` has a non-trivial `ζ`-eigenspace. The function   returns  the   index  of   a  conjugacy   class  of  `WF`  whose `ζ`-eigenspace  is  maximal  (amongst  all  `ζ`-eigenspaces of elements of `W`).  If no element of `WF`  has a non-trivial `ζ`-eigenspace the function returns `nothing`.

The  eigenvalue `ζ` can also  be specified by giving  an integer `d` (which then  specifies  `ζ=E(d)`)  or  a  fraction  `a//b`  which  then  specifies `ζ=E(b,a)`. If omitted, `ζ` is taken to be `1`.

```julia-repl
julia> W=coxgroup(:E,8)
E₈

julia> position_regular_class(W,30)
65

julia> W=complex_reflection_group(6)
G₆

julia> L=twistings(W,[2])[4]
G₆₍₂₎=G₃‚₁‚₁[ζ₄]Φ′₄

julia> position_regular_class(L,7//12)
2
```
