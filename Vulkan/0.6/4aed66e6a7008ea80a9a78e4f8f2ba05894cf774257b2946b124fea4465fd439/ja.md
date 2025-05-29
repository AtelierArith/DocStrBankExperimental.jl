拡張: VK*KHR*fragment*shading*rate

引数:

  * `sample_counts::SampleCountFlag`
  * `fragment_size::Extent2D`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRateKHR.html)

```julia
PhysicalDeviceFragmentShadingRateKHR(
    sample_counts::Vulkan.SampleCountFlag,
    fragment_size::Vulkan.Extent2D;
    next
) -> Vulkan.PhysicalDeviceFragmentShadingRateKHR

```
