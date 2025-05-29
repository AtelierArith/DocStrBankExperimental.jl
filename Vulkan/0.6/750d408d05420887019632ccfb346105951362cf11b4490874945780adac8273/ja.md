引数:

  * `map_entries::Vector{SpecializationMapEntry}`
  * `data::Ptr{Cvoid}`
  * `data_size::UInt`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSpecializationInfo.html)

```julia
SpecializationInfo(
    map_entries::AbstractArray,
    data::Ptr{Nothing};
    data_size
) -> Vulkan.SpecializationInfo

```
