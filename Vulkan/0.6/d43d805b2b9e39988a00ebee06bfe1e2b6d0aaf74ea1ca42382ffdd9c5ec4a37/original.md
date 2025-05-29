Extension: VK_KHR_fragment_shading_rate

Arguments:

  * `sample_counts::SampleCountFlag`
  * `fragment_size::_Extent2D`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRateKHR.html)

```julia
_PhysicalDeviceFragmentShadingRateKHR(
    sample_counts::Vulkan.SampleCountFlag,
    fragment_size::Vulkan._Extent2D;
    next
) -> Vulkan._PhysicalDeviceFragmentShadingRateKHR

```
