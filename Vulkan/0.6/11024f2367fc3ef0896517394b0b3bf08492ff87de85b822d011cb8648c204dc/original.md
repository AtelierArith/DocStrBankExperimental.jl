Arguments:

  * `timeline_semaphore::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceTimelineSemaphoreFeatures.html)

```julia
_PhysicalDeviceTimelineSemaphoreFeatures(
    timeline_semaphore::Bool;
    next
) -> Vulkan._PhysicalDeviceTimelineSemaphoreFeatures

```
