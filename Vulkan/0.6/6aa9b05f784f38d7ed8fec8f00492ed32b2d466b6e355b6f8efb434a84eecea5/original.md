Extension: VK_NV_copy_memory_indirect

Arguments:

  * `supported_queues::QueueFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCopyMemoryIndirectPropertiesNV.html)

```julia
_PhysicalDeviceCopyMemoryIndirectPropertiesNV(
    supported_queues::Vulkan.QueueFlag;
    next
) -> Vulkan._PhysicalDeviceCopyMemoryIndirectPropertiesNV

```
