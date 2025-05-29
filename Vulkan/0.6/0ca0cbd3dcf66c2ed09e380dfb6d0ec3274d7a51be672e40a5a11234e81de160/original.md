Extension: VK_EXT_pageable_device_local_memory

Arguments:

  * `pageable_device_local_memory::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePageableDeviceLocalMemoryFeaturesEXT.html)

```julia
_PhysicalDevicePageableDeviceLocalMemoryFeaturesEXT(
    pageable_device_local_memory::Bool;
    next
) -> Vulkan._PhysicalDevicePageableDeviceLocalMemoryFeaturesEXT

```
