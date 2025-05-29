```
GenomicInterval{T} <: AbstractGenomicInterval{T}
```

A genomic interval specifies interval with some associated metadata. The first three fields (`groupname`, `first`, and `last`) are mandatory arguments when constructing the [`Interval`](@ref Interval) object.

# Fields

  * `groupname::String`: the group name associated with the interval.
  * `first::Int64`: the leftmost position.
  * `last::Int64`: the rightmost position.
  * `strand::Strand`: the [`strand`](@ref Strand).
  * `metadata::T`
