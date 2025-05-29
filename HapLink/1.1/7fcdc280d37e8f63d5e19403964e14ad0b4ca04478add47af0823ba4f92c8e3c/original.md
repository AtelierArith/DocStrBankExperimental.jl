```
subconsensus_variations(vcf::Union{AbstractPath,AbstractString}, consensus::Haplotype)
```

Get a `Vector{Variation}` with passing variant calls from `vcf` that do not appear in `consensus`
