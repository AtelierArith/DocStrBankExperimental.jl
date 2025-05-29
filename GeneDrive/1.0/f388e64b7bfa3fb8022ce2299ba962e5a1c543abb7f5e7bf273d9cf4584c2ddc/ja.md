```
mutable struct Genetics

    all_genotypes::Array{Drive{<:Genotype}}
    likelihood::Array{Float64, 3}
    S::Vector{Float64}
    Τ::Array{Float64,3}
    Φ::Vector{Float64}
    Ξ_m::Vector{Float64}
    Ξ_f::Vector{Float64}
    Ω::Vector{Float64}
    Β::Vector{Float64}
    Η::Vector{Float64}
    all_wildtypes::Vector{Int64}
    all_modified::Vector{Int64}

        function Genetics(all_genotypes::Array{Drive{<:Genotype}})

            gN = length(all_genotypes)
            likelihood = Array{Float64, 3}(undef, gN, gN, gN)
            S = Vector{Float64}(undef, gN)
            Τ = Array{Float64,3}(undef, gN, gN, gN)
            Φ = Vector{Float64}(undef, gN)
            Ξ_m = Vector{Float64}(undef, gN)
            Ξ_f = Vector{Float64}(undef, gN)
            Ω = Vector{Float64}(undef, gN)
            Β = Vector{Float64}(undef, gN)
            Η = Vector{Float64}(undef, gN)
            all_wildtypes = Vector{Int64}(undef, gN)
            all_modified = Vector{Int64}(undef, gN)

            for (index, g) in enumerate(all_genotypes)
                likelihood[:,:,index] = g.likelihood_slice
                S[index] = g.s
                Τ[:,:,index] = g.τ
                Φ[index] = g.ϕ
                Ξ_m[index] = g.ξ_m
                Ξ_f[index] = g.ξ_f
                Ω[index] = g.ω
                Β[index] = g.β
                Η[index] = g.η
                all_wildtypes[index] = g.wildtype
                all_modified[index] = g.modified
            end

            new(all_genotypes, likelihood, S, Τ, Φ, Ξ_m, Ξ_f, Ω, Β, Η,
            all_wildtypes, all_modified)

        end

end
```

集団内のすべての遺伝子型のデータ。

# フィールド

  * `all_genotypes::Array{Drive{<:Genotype}}`: 集団内のすべての遺伝子型。
  * `likelihood::Array{Float64, 3}`: 遺伝子型ごとの子孫の可能性。
  * `S::Vector{Float64}`: 卵産みに適用される遺伝子型ごとの乗算的繁殖修正因子。
  * `Τ::Array{Float64,3}`: 卵産みに適用される遺伝子型ごとの子孫の生存率。
  * `Φ::Vector{Float64}`: 遺伝子型ごとのオスからメスへの出現比率。
  * `Ξ_m::Vector{Float64}`: 遺伝子型ごとのオスの幼虫成功率。
  * `Ξ_f::Vector{Float64}`: 遺伝子型ごとのメスの幼虫成功率。
  * `Ω::Vector{Float64}`: 遺伝子型ごとの乗算的成虫死亡率修正因子。
  * `Β::Vector{Float64}`: 遺伝子型ごとのメスの繁殖能力（産卵数）。
  * `Η::Vector{Float64}`: 遺伝子型ごとのオスの交配適応度。
  * `all_wildtypes::Vector{Int64}`: ホモ接合体の野生型ブール値を収集。
  * `all_modified::Vector{Int64}`: ホモ接合体の修正型ブール値を収集。
