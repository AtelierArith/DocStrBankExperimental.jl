Extension: VK_EXT_robustness2

Arguments:

  * `robust_buffer_access_2::Bool`
  * `robust_image_access_2::Bool`
  * `null_descriptor::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRobustness2FeaturesEXT.html)

```julia
_PhysicalDeviceRobustness2FeaturesEXT(
    robust_buffer_access_2::Bool,
    robust_image_access_2::Bool,
    null_descriptor::Bool;
    next
) -> Vulkan._PhysicalDeviceRobustness2FeaturesEXT

```
