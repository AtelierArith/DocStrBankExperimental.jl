Extension: VK_KHR_push_descriptor

Arguments:

  * `max_push_descriptors::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePushDescriptorPropertiesKHR.html)

```julia
_PhysicalDevicePushDescriptorPropertiesKHR(
    max_push_descriptors::Integer;
    next
) -> Vulkan._PhysicalDevicePushDescriptorPropertiesKHR

```
