`Zbasedring(f::Family)` または `Zbasedring(S,special=1)`

Chevie のすべてのフーリエ行列 `S` はユニタリであり、すなわち `S⁻¹=conj(S)` であり、特別な行 `s` (ファミリー `f` に対するインデックス `s=special(f)` の行) を持ち、その行のエントリ `Sₛ,ᵢ` は `0` に等しくない。さらに、和 `Cᵢ,ⱼ,ₖ=sumₗ Sᵢ,ₗ  Sⱼ,ₗ conj(Sₖ,ₗ)/Sₛ,ₗ` は整数値を取る性質を持つ。最後に、`S` は複素共役が `S` の行の符号付きの置換 `σ` を行う性質を持つ。

したがって、次のように `ℤ`-代数 `A` を定義することができる：それは `S` の行によってインデックス付けされた基底 `bᵢ` を持ち、`bᵢbⱼ` の `bₖ` における係数が `Cᵢ,ⱼ,ₖ` に等しいという事実によって乗法が定義される。この代数は、ファミリー `f` またはそのフーリエ行列と特別な行の数を与えることによって指定することができる。

`A` は可換であり、単位元は要素 `bₛ` である；基底 σ(bᵢ)`は`線形形式 (bᵢ,bⱼ)=Cᵢ,ⱼ,σ₍ₛ₎` に対して双対である。

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
