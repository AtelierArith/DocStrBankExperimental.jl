```
mutable struct ProportionalRelease <: Intervention
    node::Symbol
    organism::Type{<:Species}
    stage::Type{<:LifeStage}
    gene_index::Int64
    times::Vector{Float64}
    proportion::Float64
    callbacks::Vector
    adults_counting::String
end
```

修正された生物を放出することに基づく生物制御介入のデータ。

# 引数

  * `node::Symbol`: 放出が行われる`Node`。
  * `organism::Type{<:Species}`: 放出される生物の種。
  * `stage::Type{<:LifeStage}`: 放出される生物の`LifeStage`。
  * `gene_index::Int64`: 介入を実施するために放出される遺伝子型。
  * `times::Vector{Float64}`: 放出の時間点。
  * `proportion::Float64`: 各時間帯に放出される修正された生物の割合。
  * `callbacks::Vector`
  * `adults_to_count::String`: 比例放出サイズを測定するための既存の個体群の`LifeStage`。選択肢には`Male`、`Female`、または`All`が含まれます。
