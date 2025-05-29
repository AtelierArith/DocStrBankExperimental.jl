拡張: VK*KHR*dynamic_rendering

引数:

  * `per_view_attributes::Bool`
  * `per_view_attributes_position_x_only::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultiviewPerViewAttributesInfoNVX.html)

```julia
MultiviewPerViewAttributesInfoNVX(
    per_view_attributes::Bool,
    per_view_attributes_position_x_only::Bool;
    next
) -> Vulkan.MultiviewPerViewAttributesInfoNVX

```
