```
fd_pnsystem
```

すべてのタイプの `PNSystem` に関する象徴的な情報を含む象徴的な `PNSystem` です。

特に、このオブジェクトは（本質的に）無限の `PNOrder` を持ち、`Λ₁` や `Λ₂` のような量に対して非ゼロの値を持ち、最終的な出力が `Float64` であると仮定しています。異なる選択肢が必要な場合は、[`FDPNSystem`](@ref) を自分で呼び出すか、異なる専門のサブタイプの `PNSystem` を構築する必要があるかもしれません（それほど難しくはありません）。

# 例

```jldoctest
julia> using PostNewtonian: M₁, M₂, χ⃗₁, χ⃗₂, FDPNSystem

julia> fd_pnsystem = FDPNSystem(Float64)
FDPNSystem{Float64, 9223372036854775805//2}(FastDifferentiation.Node[M₁, M₂, χ⃗₁ˣ, χ⃗₁ʸ, χ⃗₁ᶻ, χ⃗₂ˣ, χ⃗₂ʸ, χ⃗₂ᶻ, Rʷ, Rˣ, Rʸ, Rᶻ, v, Φ], Λ₁, Λ₂)

julia> M₁(fd_pnsystem), M₂(fd_pnsystem)
(M₁, M₂)

julia> χ⃗₁(fd_pnsystem)
 + χ⃗₁ˣ𝐢 + χ⃗₁ʸ𝐣 + χ⃗₁ᶻ𝐤

julia> χ⃗₂(fd_pnsystem)
 + χ⃗₂ˣ𝐢 + χ⃗₂ʸ𝐣 + χ⃗₂ᶻ𝐤
```
