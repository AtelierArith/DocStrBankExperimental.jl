```
quality(vc::VariationCall) -> Union{Nothing,Float64}
```

Gets the average phred quality score of `vc`, if known. Returns `nothing` if unknown.

See also [`quality(::VariationInfo)`](@ref), [`quality(::VariationPileup)`](@ref)
