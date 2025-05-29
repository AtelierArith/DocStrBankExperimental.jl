```
kratio(unk::Spectrum, std::Spectrum, back1::AbstractUnitRange{<:Integer}, peak::AbstractUnitRange{<:Integer}, back2::AbstractUnitRange{<:Integer})::UncertainValue
kratio(unk::Spectrum, std::Spectrum, back1::StepRangeLen{Float64}, peak::StepRangeLen{Float64}, back2::StepRangeLen{Float64})::UncertainValue
```

unkに対するk比は、標準に対して線量で補正されます。`unk`と`std`には、`:LiveTime`および`:ProbeCurrent`のプロパティが定義されている必要があります。
