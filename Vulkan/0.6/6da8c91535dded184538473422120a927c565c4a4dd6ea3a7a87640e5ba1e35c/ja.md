拡張: VK*EXT*debug_marker

引数:

  * `marker_name::String`
  * `color::NTuple{4, Float32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerMarkerInfoEXT.html)

```julia
_DebugMarkerMarkerInfoEXT(
    marker_name::AbstractString,
    color::NTuple{4, Float32};
    next
) -> Vulkan._DebugMarkerMarkerInfoEXT

```
