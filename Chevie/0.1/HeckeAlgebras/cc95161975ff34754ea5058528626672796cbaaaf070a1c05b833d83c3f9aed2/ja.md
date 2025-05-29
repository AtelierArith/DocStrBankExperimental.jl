`CharTable(H::HeckeAlgebra or HeckeCoset)`

は、Hecke代数 `H` の `CharTable` を返します。原始群 `G₃₁,  G₃₂,  G₃₄` には、欠落した表現に対応する `missing` エントリがあります（詳細は [`representation`](@ref) を参照）。`CharTable` の列は `classnames(H.W)` によってラベル付けされ、対応する要素のキャラクタ値が `classreps(H.W)` によって与えられます。

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
