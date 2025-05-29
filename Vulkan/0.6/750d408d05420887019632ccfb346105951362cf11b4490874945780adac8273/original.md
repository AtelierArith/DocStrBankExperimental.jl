Arguments:

  * `map_entries::Vector{SpecializationMapEntry}`
  * `data::Ptr{Cvoid}`
  * `data_size::UInt`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSpecializationInfo.html)

```julia
SpecializationInfo(
    map_entries::AbstractArray,
    data::Ptr{Nothing};
    data_size
) -> Vulkan.SpecializationInfo

```
