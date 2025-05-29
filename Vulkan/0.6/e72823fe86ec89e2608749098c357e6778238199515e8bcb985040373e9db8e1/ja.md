拡張: VK*KHR*present_id

引数:

  * `present_id::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePresentIdFeaturesKHR.html)

```julia
_PhysicalDevicePresentIdFeaturesKHR(
    present_id::Bool;
    next
) -> Vulkan._PhysicalDevicePresentIdFeaturesKHR

```
