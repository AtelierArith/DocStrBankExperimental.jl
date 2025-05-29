```
    struct sEF
```

効率的フロンティア、フィールド：

```
        Ap::Matrix{Float64}     # v=a₂μ²+a₁μ+a₀、各行 [a₂ a₁ a₀]
        mu::Vector{Float64}     #より高い平均
        sgm::Vector{Float64}    #より高いシグマ
        Z::Matrix{Float64}      #ウェイト、各コーナーポートフォリオが1行
        ic::Vector{Int}       #関連するクリティカルラインのID
```
