拡張: VK*EXT*robustness2

引数:

  * `robust_buffer_access_2::Bool`
  * `robust_image_access_2::Bool`
  * `null_descriptor::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRobustness2FeaturesEXT.html)

```julia
PhysicalDeviceRobustness2FeaturesEXT(
    robust_buffer_access_2::Bool,
    robust_image_access_2::Bool,
    null_descriptor::Bool;
    next
) -> Vulkan.PhysicalDeviceRobustness2FeaturesEXT

```
