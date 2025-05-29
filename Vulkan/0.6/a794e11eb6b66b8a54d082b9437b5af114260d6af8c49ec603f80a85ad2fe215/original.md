Extension: VK_NV_fragment_shading_rate_enums

Arguments:

  * `max_fragment_shading_rate_invocation_count::SampleCountFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRateEnumsPropertiesNV.html)

```julia
_PhysicalDeviceFragmentShadingRateEnumsPropertiesNV(
    max_fragment_shading_rate_invocation_count::Vulkan.SampleCountFlag;
    next
) -> Vulkan._PhysicalDeviceFragmentShadingRateEnumsPropertiesNV

```
