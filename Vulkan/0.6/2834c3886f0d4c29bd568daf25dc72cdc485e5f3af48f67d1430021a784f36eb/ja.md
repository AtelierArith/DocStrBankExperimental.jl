引数:

  * `map_entries::Vector{_SpecializationMapEntry}`
  * `data::Ptr{Cvoid}`
  * `data_size::UInt`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSpecializationInfo.html)

```julia
_SpecializationInfo(
    map_entries::AbstractArray,
    data::Ptr{Nothing};
    data_size
) -> Vulkan._SpecializationInfo

```
