```
subconsensus_variations(vcf::Union{AbstractPath,AbstractString}, consensus::Haplotype)
```

`consensus`に現れない`vcf`からの合格した変異コールを持つ`Vector{Variation}`を取得します。
