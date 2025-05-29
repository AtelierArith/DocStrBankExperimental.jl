Extension: VK_EXT_validation_flags

Arguments:

  * `disabled_validation_checks::Vector{ValidationCheckEXT}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationFlagsEXT.html)

```julia
ValidationFlagsEXT(
    disabled_validation_checks::AbstractArray;
    next
) -> Vulkan.ValidationFlagsEXT

```
