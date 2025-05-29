Extension: VK_EXT_debug_utils

Arguments:

  * `label_name::String`
  * `color::NTuple{4, Float32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsLabelEXT.html)

```julia
_DebugUtilsLabelEXT(
    label_name::AbstractString,
    color::NTuple{4, Float32};
    next
) -> Vulkan._DebugUtilsLabelEXT

```
