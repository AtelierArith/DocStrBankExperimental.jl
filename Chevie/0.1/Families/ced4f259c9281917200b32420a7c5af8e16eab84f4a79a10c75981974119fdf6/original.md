`Zbasedring(f::Family)` or `Zbasedring(S,special=1)`

All  the Fourier matrices `S` in Chevie are unitary, that is `S⁻¹=conj(S)`, and  have a  *special* line  `s` (the  line of  index `s=special(f)`  for a family  `f`) such that no entry `Sₛ,ᵢ`  is equal to `0`. Further, they have the  property that  the sums  `Cᵢ,ⱼ,ₖ=sumₗ Sᵢ,ₗ  Sⱼ,ₗ conj(Sₖ,ₗ)/Sₛ,ₗ` take integral  values. Finally,  `S` has  the property  that complex conjugation does a permutation with signs `σ` of the lines of `S`.

It  follows that we can define a `ℤ`-algebra `A` as follows: it has a basis `bᵢ`  indexed by the lines of `S`,  and has a multiplication defined by the fact  that the  coefficient of  `bᵢbⱼ` on  `bₖ` is  equal to `Cᵢ,ⱼ,ₖ`. This algebra  can be specified by giving a family `f` or just its Fourier matrix and the number of its special line.

`A`  is commutative, and has as unit  the element `bₛ`; the basis σ(bᵢ)`is`dual to `bᵢ` for the linear form (bᵢ,bⱼ)=Cᵢ,ⱼ,σ₍ₛ₎`.

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> uc=UnipotentCharacters(W);f=uc.families[4];

julia> A=Zbasedring(fourier(f),1)
ℤ-based ring dim.5

julia> b=basis(A)
5-element Vector{AlgebraElt{Chevie.Families.ZBasedRing, Int64}}:
 B₁
 B₂
 B₃
 B₄
 B₅

julia> b*permutedims(b)
5×5 Matrix{AlgebraElt{Chevie.Families.ZBasedRing, Int64}}:
 B₁  B₂      B₃      B₄        B₅
 B₂  -B₄+B₅  B₁+B₄   B₂-B₃     B₃
 B₃  B₁+B₄   -B₄+B₅  -B₂+B₃    B₂
 B₄  B₂-B₃   -B₂+B₃  B₁+B₄-B₅  -B₄
 B₅  B₃      B₂      -B₄       B₁

julia> CharTable(A)
CharTable(ℤ-based ring dim.5)
┌─┬─────────────────┐
│ │1    2    3  4  5│
├─┼─────────────────┤
│1│1  √-3 -√-3  2 -1│
│2│1    1    1  .  1│
│3│1   -1   -1  .  1│
│4│1    .    . -1 -1│
│5│1 -√-3  √-3  2 -1│
└─┴─────────────────┘
```
