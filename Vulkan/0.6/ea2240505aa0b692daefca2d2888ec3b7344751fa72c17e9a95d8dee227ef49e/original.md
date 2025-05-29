Extension: VK_KHR_present_wait

Arguments:

  * `present_wait::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePresentWaitFeaturesKHR.html)

```julia
_PhysicalDevicePresentWaitFeaturesKHR(
    present_wait::Bool;
    next
) -> Vulkan._PhysicalDevicePresentWaitFeaturesKHR

```
