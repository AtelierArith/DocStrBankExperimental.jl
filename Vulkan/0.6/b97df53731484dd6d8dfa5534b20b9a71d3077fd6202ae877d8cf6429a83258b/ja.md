拡張: VK*EXT*validation_flags

引数:

  * `disabled_validation_checks::Vector{ValidationCheckEXT}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationFlagsEXT.html)

```julia
_ValidationFlagsEXT(
    disabled_validation_checks::AbstractArray;
    next
) -> Vulkan._ValidationFlagsEXT

```
