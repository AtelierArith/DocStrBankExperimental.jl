拡張: VK*EXT*conditional_rendering

引数:

  * `conditional_rendering::Bool`
  * `inherited_conditional_rendering::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceConditionalRenderingFeaturesEXT.html)

```julia
_PhysicalDeviceConditionalRenderingFeaturesEXT(
    conditional_rendering::Bool,
    inherited_conditional_rendering::Bool;
    next
) -> Vulkan._PhysicalDeviceConditionalRenderingFeaturesEXT

```
