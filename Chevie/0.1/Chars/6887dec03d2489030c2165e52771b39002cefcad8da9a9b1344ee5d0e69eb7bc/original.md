`induction_table(u,g)`

returns   an  object  describing  the   decomposition  of  the  irreducible characters  of the subgroup  `u` induced to  the group `g`.  At the repl or IJulia  or Pluto,  a table  is displayed  where the  rows correspond to the characters  of the parent group, and the  columns to those of the subgroup. The  returned  object  has  a  field  `scalar`  which  is  a  `Matrix{Int}` containing  the  induction  table,  and  the  other fields contain labeling information taken from the character tables of `u` and `g` when it exists.

```julia-rep1
julia> g=Group([Perm(1,2),Perm(2,3),Perm(3,4)])
Group([(1,2),(2,3),(3,4)])

julia> u=Group( [ Perm(1,2), Perm(3,4) ])
Group([(1,2),(3,4)])

julia> induction_table(u,g)  #     needs "using GAP"
Induction table from Group((1,2),(3,4)) to Group((1,2),(2,3),(3,4))
┌───┬───────────────┐
│   │X.1 X.2 X.3 X.4│
├───┼───────────────┤
│X.1│  .   1   .   .│
│X.2│  .   1   1   1│
│X.3│  1   1   .   .│
│X.4│  1   .   1   1│
│X.5│  1   .   .   .│
└───┴───────────────┘
```

```julia-repl
julia> g=coxgroup(:G,2)
G₂

julia> u=reflection_subgroup(g,[1,6])
G₂₍₁₅₎=A₂

julia> t=induction_table(u,g)
Induction table from G₂₍₁₅₎=A₂ to G₂
┌─────┬────────┐
│     │111 21 3│
├─────┼────────┤
│φ₁‚₀ │  .  . 1│
│φ₁‚₆ │  1  . .│
│φ′₁‚₃│  1  . .│
│φ″₁‚₃│  .  . 1│
│φ₂‚₁ │  .  1 .│
│φ₂‚₂ │  .  1 .│
└─────┴────────┘
```

`IO` attributes can be transmitted to the table format method

```julia-rep1
julia> xdisplay(t;rows=[5],cols=[3,2])
Induction table from G₂₍₁₅₎=A₂ to G₂
┌─────┬────┐
│     │3 21│
├─────┼────┤
│φ₂‚₁ │.  1│
└─────┴────┘
```

It is also possible to TeX induction tables with `xdisplay(t;TeX=true)`.

`induction_table` also works for spets (reflection cosets).
