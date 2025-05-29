```
HaplotypeCall{S,T}
```

A `Haplotype` that has had linkage disequilibrium calculations performed along with metadata to verify or refute its validity. Very similar to a [`VariationCall`](@ref), but for `Haplotype`s.

# Fields

  * `depth::UInt64`: How many sequencing reads contain all the `Variation`s in `haplotype`
  * `linkage::Float64`: The unweighted linkage disequilibrium coefficient of this call
  * `frequency::Float64`: How often this haplotype occurs compared to the entire read pool
  * `significance::Float64`: The $χ^2$ statistical significance ($p$-value) of this call
  * `haplotype::Haplotype{S,T}`: The set of `Variation`s that are inherited together in this   call
