拡張: VK*KHR*fragment*shading*rate

引数:

  * `sample_counts::SampleCountFlag`
  * `fragment_size::_Extent2D`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRateKHR.html)

```julia
_PhysicalDeviceFragmentShadingRateKHR(
    sample_counts::Vulkan.SampleCountFlag,
    fragment_size::Vulkan._Extent2D;
    next
) -> Vulkan._PhysicalDeviceFragmentShadingRateKHR

```
