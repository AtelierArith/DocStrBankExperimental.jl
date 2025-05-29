```
Corpus{T<:NamedTuple,D}
```

A corpus is a collection of [`Document`](@ref)s, along with some metadata. It has two fields,

  * `documents::Vector{Document{D}}`
  * `metadata::T`

Note each `Document` in a `Corpus` must have metadata of the same type.
