```
mutable struct Release <: Intervention
    node::Symbol
    organism::Type{<:Species}
    stage::Type{<:LifeStage}
    gene_index::Int64
    times::Vector{Float64}
    values::Vector{Float64}
    callbacks::Vector
end
```

修正された生物を放出することに基づく生物制御介入のデータ。抑制技術と置換技術の両方に適用可能です。

# 引数

  * `node::Symbol`: 放出が行われる`Node`。
  * `organism::Type{<:Species}`: 放出される生物の種。
  * `stage::Type{<:LifeStage}`: 放出される生物の`Life stage`。
  * `gene_index::Int64`: 介入を実施するために放出される遺伝子型。
  * `times::Vector{Float64}`: 放出の時間点。
  * `values::Union{Float64, Vector{Float64}}`: 各時間帯に放出される修正された生物の数。可変サイズの放出が許可されています。
  * `callbacks::Vector`
