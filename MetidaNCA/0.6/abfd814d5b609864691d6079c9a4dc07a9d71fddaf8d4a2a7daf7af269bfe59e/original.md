```
PKSubject(time::Vector{T}, conc::Vector{O}, kelauto::Bool, kelrange::ElimRange, dosetime::DoseTime, keldata::KelData, id::Dict{Symbol, V} = Dict{Symbol, Any}()) where T <: Number where O <: Union{Number, Missing} where V
```

Pharmacokinetic subject.

Fields:

  * time::Vector{T} - time values;
  * obs::Vector{O} - observations;
  * kelauto::Bool
  * kelrange::ElimRange
  * dosetime::DoseTime
  * keldata::KelData
  * id::Dict{Symbol, V}
