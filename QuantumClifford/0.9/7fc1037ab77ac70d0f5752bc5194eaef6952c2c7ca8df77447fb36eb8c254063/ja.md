非可換のパウリの集合に対して、対 Aₖ, Bₖ が反交換し、他のすべてのペアが交換する形の生成集合 ⟨A₁, A₂, ... Aₖ, Aₖ₊₁, ... Aₘ, B₁, B₂, ... Bₖ⟩ を返します。これは [RevModPhys.87.307](@cite) に基づいています。

生成集合は [`SubsystemCodeTableau`](@ref) 型のデータ構造として返されます。`logicalxview` 関数は ⟨A₁, A₂,... Aₖ⟩ を返し、`logicalzview` 関数は ⟨B₁, B₂, ... Bₖ⟩ を返します。`stabilizerview` は ⟨Aₖ₊₁, ... Aₘ⟩ を安定器として返し、`destabilizerview` はその安定器の不安定器を返します。

この正準化では位相がゼロにされます。

```jldoctest
julia> canonicalize_noncomm(T"XX XZ XY")
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z_
𝒳━━
+ XX
𝒮𝓉𝒶𝒷
+ X_
𝒵━━
+ XZ
```
