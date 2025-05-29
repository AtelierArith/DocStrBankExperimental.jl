```
PKSubject(time::Vector{T}, conc::Vector{O}, kelauto::Bool, kelrange::ElimRange, dosetime::DoseTime, keldata::KelData, id::Dict{Symbol, V} = Dict{Symbol, Any}()) where T <: Number where O <: Union{Number, Missing} where V
```

薬物動態の対象。

フィールド:

  * time::Vector{T} - 時間の値;
  * obs::Vector{O} - 観測値;
  * kelauto::Bool
  * kelrange::ElimRange
  * dosetime::DoseTime
  * keldata::KelData
  * id::Dict{Symbol, V}
