```julia
mutable struct StepNumberTune{T<:BaytesCore.UpdateBool}
```

MCMCアルゴリズムにおける離散化ステップの数に関する情報を含みます。

# フィールド

  * `adaption::BaytesCore.UpdateBool`: trueの場合、ステップ数が適応されます。
  * `steps::Int64`: 離散化ステップの数。
  * `stepsᵐᵃˣ::Int64`: 離散化ステップの最大数。
  * `∫dt::Float64`: 希望する積分時間。
