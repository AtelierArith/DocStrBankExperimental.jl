Extension: VK_KHR_present_id

Arguments:

  * `present_id::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePresentIdFeaturesKHR.html)

```julia
_PhysicalDevicePresentIdFeaturesKHR(
    present_id::Bool;
    next
) -> Vulkan._PhysicalDevicePresentIdFeaturesKHR

```
