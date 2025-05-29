```
    aEF = eFrontier(aCL::Vector{sCL{T}}, PS::Problem{T}; nS=Settings(PS)) where T
```

ステータスセグメント法によるフル効率的フロンティアを計算します。

返される aEF は以下の構造を持ちます。

```
    struct sEF    #効率的フロンティア       Float64 は OK
        Ap::Matrix{Float64}     # v=a₂μ²+a₁μ+a₀, 各行 [a₂ a₁ a₀]
        mu::Vector{Float64}     #より高い平均
        sgm::Vector{Float64}    #より高いシグマ
        Z::Matrix{Float64}      #ウェイト、各コーナーポートフォリオが1行
        ic::Vector{Int}         #関連するクリティカルラインのID
    end
```

[`EfficientFrontier.ECL`](@ref)、[`ePortfolio`](@ref)、[`Problem`](@ref)、[`Settings`](@ref) も参照してください。
