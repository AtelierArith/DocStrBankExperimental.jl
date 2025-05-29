拡張: VK*KHR*fragment*shading*rate

引数:

  * `pipeline_fragment_shading_rate::Bool`
  * `primitive_fragment_shading_rate::Bool`
  * `attachment_fragment_shading_rate::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRateFeaturesKHR.html)

```julia
_PhysicalDeviceFragmentShadingRateFeaturesKHR(
    pipeline_fragment_shading_rate::Bool,
    primitive_fragment_shading_rate::Bool,
    attachment_fragment_shading_rate::Bool;
    next
) -> Vulkan._PhysicalDeviceFragmentShadingRateFeaturesKHR

```
