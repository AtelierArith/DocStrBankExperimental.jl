```
strand_bias(vc::VariationCall) -> Union{Nothing,Float64}
```

Gets the fraction of times `vc` appears on the positive strand. Returns `nothing` if unknown.

See also [`strand(::VariationInfo)`](@ref), [`strand(::VariationPileup)`](@ref)
