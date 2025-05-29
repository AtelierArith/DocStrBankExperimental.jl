```julia
struct Branch{Tkind, Tprob, T<:Union{BifurcationKit.ContResult, Vector{BifurcationKit.ContResult}}, Tbp} <: BifurcationKit.AbstractResult{Tkind, Tprob}
```

Branchは、分岐点から分岐するブランチの計算結果をカプセル化する構造体です。

  * `γ::Union{BifurcationKit.ContResult, Vector{BifurcationKit.ContResult}}`: 分岐点`bp`から分岐するブランチの集合
  * `bp::Any`: 分岐点。これはγのブランチの根と考えられています。
