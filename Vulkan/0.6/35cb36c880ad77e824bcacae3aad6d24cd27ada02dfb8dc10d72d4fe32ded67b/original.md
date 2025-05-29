Extension: VK_EXT_conditional_rendering

Arguments:

  * `conditional_rendering::Bool`
  * `inherited_conditional_rendering::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceConditionalRenderingFeaturesEXT.html)

```julia
_PhysicalDeviceConditionalRenderingFeaturesEXT(
    conditional_rendering::Bool,
    inherited_conditional_rendering::Bool;
    next
) -> Vulkan._PhysicalDeviceConditionalRenderingFeaturesEXT

```
