Extension: VK_KHR_fragment_shading_rate

Arguments:

  * `pipeline_fragment_shading_rate::Bool`
  * `primitive_fragment_shading_rate::Bool`
  * `attachment_fragment_shading_rate::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRateFeaturesKHR.html)

```julia
PhysicalDeviceFragmentShadingRateFeaturesKHR(
    pipeline_fragment_shading_rate::Bool,
    primitive_fragment_shading_rate::Bool,
    attachment_fragment_shading_rate::Bool;
    next
) -> Vulkan.PhysicalDeviceFragmentShadingRateFeaturesKHR

```
