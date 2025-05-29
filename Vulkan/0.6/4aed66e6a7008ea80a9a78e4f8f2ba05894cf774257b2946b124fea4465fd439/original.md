Extension: VK_KHR_fragment_shading_rate

Arguments:

  * `sample_counts::SampleCountFlag`
  * `fragment_size::Extent2D`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRateKHR.html)

```julia
PhysicalDeviceFragmentShadingRateKHR(
    sample_counts::Vulkan.SampleCountFlag,
    fragment_size::Vulkan.Extent2D;
    next
) -> Vulkan.PhysicalDeviceFragmentShadingRateKHR

```
