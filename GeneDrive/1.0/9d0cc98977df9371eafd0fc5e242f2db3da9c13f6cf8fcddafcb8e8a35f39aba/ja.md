```
mutable struct Drive{G <: Genotype}
    genotype::Type{G}
    likelihood_slice::Array{Float64,2}
    s::Float64
    τ::Array{Float64,2}
    ϕ::Float64
    ξ_m::Float64
    ξ_f::Float64
    ω::Float64
    β::Float64
    η::Float64
    wildtype::Int64
    modified::Int64
end
```

個々の遺伝子型のデータ。

# フィールド

  * `genotype::Type{G}`: 単一の遺伝子型。
  * `likelihood_slice::Array{Float64,2}`: この遺伝子型の子孫の可能性。
  * `s::Float64`: 乗法的な繁殖修正因子。
  * `τ::Array{Float64,2}`: 子孫の生存率。
  * `ϕ::Float64`: オスからメスへの出現比率。
  * `ξ_m::Float64`: オスの幼虫成功率。
  * `ξ_f::Float64`: メスの幼虫成功率。
  * `ω::Float64`: 乗法的な成虫死亡率修正因子。
  * `β::Float64`: メスの繁殖能力。
  * `η::Float64`: オスの交配適応度。
  * `wildtype::Int64`: ブール値がホモ接合劣性を示す。
  * `modified::Int64`: ブール値がホモ接合修正を示す。
