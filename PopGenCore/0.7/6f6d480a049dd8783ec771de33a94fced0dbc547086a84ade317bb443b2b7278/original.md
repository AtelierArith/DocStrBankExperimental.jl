```
ishet(locus::T) where T <: GenoArray
ishet(locus::Genotype)
ishet(locus::Missing)
```

A series of methods to test if a locus or loci are heterozygous and return `true` if it is, `false` if it isn't (or missing). For calculations, we recommend using `_ishet()`, which returns `missing` if the genotype is `missing`. The vector version simply maps the function over the elements.
