Arguments:

  * `queue_family_properties::_QueueFamilyProperties`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyProperties2.html)

```julia
_QueueFamilyProperties2(
    queue_family_properties::Vulkan._QueueFamilyProperties;
    next
) -> Vulkan._QueueFamilyProperties2

```
