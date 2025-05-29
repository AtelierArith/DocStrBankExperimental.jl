`CharTable(H::HeckeAlgebra or HeckeCoset)`

returns  the `CharTable` of the Hecke algebra `H`. For the primitive groups `G₃₁,  G₃₂,  G₃₄`  there  are  `missing` entries corresponding to missing representations   (see  [`representation`](@ref)).   The  columns   of  the `CharTable`  are labelled  by `classnames(H.W)`  and contain  the character values for the corresponding element given by `classreps(H.W)`.

```julia-repl
julia> H=hecke(crg(4),Pol())
hecke(G₄,q)

julia> CharTable(H)
CharTable(hecke(G₄,q))
┌────┬──────────────────────────────────────┐
│    │.    z 212   12    z12     1        1z│
├────┼──────────────────────────────────────┤
│φ₁‚₀│1   q⁶  q³   q²     q⁸     q        q⁷│
│φ₁‚₄│1    1   1  ζ₃²    ζ₃²    ζ₃        ζ₃│
│φ₁‚₈│1    1   1   ζ₃     ζ₃   ζ₃²       ζ₃²│
│φ₂‚₅│2   -2   .    1     -1    -1         1│
│φ₂‚₃│2 -2q³   . ζ₃²q -ζ₃²q⁴ q+ζ₃² -q⁴-ζ₃²q³│
│φ₂‚₁│2 -2q³   .  ζ₃q  -ζ₃q⁴  q+ζ₃  -q⁴-ζ₃q³│
│φ₃‚₂│3  3q²  -q    .      .   q-1     q³-q²│
└────┴──────────────────────────────────────┘
```
