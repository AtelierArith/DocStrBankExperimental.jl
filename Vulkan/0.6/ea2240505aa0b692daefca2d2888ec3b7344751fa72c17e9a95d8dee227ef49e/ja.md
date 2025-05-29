拡張: VK*KHR*present_wait

引数:

  * `present_wait::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePresentWaitFeaturesKHR.html)

```julia
_PhysicalDevicePresentWaitFeaturesKHR(
    present_wait::Bool;
    next
) -> Vulkan._PhysicalDevicePresentWaitFeaturesKHR

```
