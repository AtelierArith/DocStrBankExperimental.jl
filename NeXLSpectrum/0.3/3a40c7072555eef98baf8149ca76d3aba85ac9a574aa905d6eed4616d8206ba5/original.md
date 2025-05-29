```
kratio(unk::Spectrum, std::Spectrum, back1::AbstractUnitRange{<:Integer}, peak::AbstractUnitRange{<:Integer}, back2::AbstractUnitRange{<:Integer})::UncertainValue
kratio(unk::Spectrum, std::Spectrum, back1::StepRangeLen{Float64}, peak::StepRangeLen{Float64}, back2::StepRangeLen{Float64})::UncertainValue
```

The k-ratio of unk relative to std corrected for dose.  Requires that `unk` and `std` have the properties `:LiveTime` and `:ProbeCurrent` defined.
