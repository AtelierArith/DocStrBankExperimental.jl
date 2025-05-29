```
Genotype::DataType
```

For convenience purposes, an alias for `NTuple{N, <:Signed} where N`, which is the type describing individual genotypes in PopData. Specifically, there exist `SNP` as an alias for `NTuple{N, Int8}` and `MSat` for `NTuple{N, Int16}`
