Specification authors.

```julia
struct Authors <: VulkanSpec.Collection{VulkanSpec.AuthorTag}
```

  * `data::StructArrays.StructVector{VulkanSpec.AuthorTag, @NamedTuple{tag::Vector{String}, author::Vector{String}}, Int64}`
