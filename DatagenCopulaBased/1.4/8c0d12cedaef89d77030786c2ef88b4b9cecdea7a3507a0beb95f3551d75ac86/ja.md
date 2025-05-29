```
MarshallOlkinCopula
```

フィールド:

  * n::Int - マージナルの数
  * λ::Vector{Real} - 非負パラメータ λₛ のベクトル、すなわち:   λ = [λ₁, λ₂, ..., λₙ, λ₁₂, λ₁₃, ..., λ₁ₙ, λ₂₃, ..., λₙ₋₁ₙ, λ₁₂₃, ..., λ₁₂...ₙ]   そして n = ceil(Int, log(2, length(λ)-1))。

コンストラクタ

```
MarshallOlkinCopula(λ)
```

length(λ) ≧ 3 が必要です

```jldoctest
julia> MarshallOlkinCopula([0.5, 0.5, 0.6])
MarshallOlkinCopula(2, [0.5, 0.5, 0.6])

julia> MarshallOlkinCopula([0.5, 0.5, 0.6, 0.7, 0.7, 0.7, 0.8])
MarshallOlkinCopula(3, [0.5, 0.5, 0.6, 0.7, 0.7, 0.7, 0.8])
```
