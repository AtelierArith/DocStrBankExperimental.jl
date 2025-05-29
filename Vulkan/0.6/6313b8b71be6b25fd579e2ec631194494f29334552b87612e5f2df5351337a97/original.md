Extension: VK_EXT_debug_marker

Arguments:

  * `marker_name::String`
  * `color::NTuple{4, Float32}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerMarkerInfoEXT.html)

```julia
DebugMarkerMarkerInfoEXT(
    marker_name::AbstractString,
    color::NTuple{4, Float32};
    next
) -> Vulkan.DebugMarkerMarkerInfoEXT

```
