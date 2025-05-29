```
ishom(locus::T) where T <: GenoArray
ishom(locus::T) where T<:Base.SkipMissing
ishom(locus::Genotype)
ishom(locus::Missing)
```

A series of methods to test if a locus or loci are homozygous and return `true` if it is, `false` if it isn't (or missing). For calculations, we recommend using `_ishom()`, which returns `missing` if the genotype is `missing`. The vector methods simply map the function over the elements. Haploid genotypes return `false`.
