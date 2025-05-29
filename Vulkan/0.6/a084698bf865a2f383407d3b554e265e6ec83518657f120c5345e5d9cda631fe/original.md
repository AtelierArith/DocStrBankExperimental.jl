Extension: VK_KHR_dynamic_rendering

Arguments:

  * `per_view_attributes::Bool`
  * `per_view_attributes_position_x_only::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultiviewPerViewAttributesInfoNVX.html)

```julia
_MultiviewPerViewAttributesInfoNVX(
    per_view_attributes::Bool,
    per_view_attributes_position_x_only::Bool;
    next
) -> Vulkan._MultiviewPerViewAttributesInfoNVX

```
