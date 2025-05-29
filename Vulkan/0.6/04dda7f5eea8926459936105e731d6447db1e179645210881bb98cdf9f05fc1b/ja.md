拡張: VK*EXT*debug_utils

引数:

  * `label_name::String`
  * `color::NTuple{4, Float32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsLabelEXT.html)

```julia
_DebugUtilsLabelEXT(
    label_name::AbstractString,
    color::NTuple{4, Float32};
    next
) -> Vulkan._DebugUtilsLabelEXT

```
