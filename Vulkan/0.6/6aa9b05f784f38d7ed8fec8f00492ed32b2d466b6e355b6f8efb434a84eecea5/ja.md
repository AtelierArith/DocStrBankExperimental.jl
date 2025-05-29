拡張: VK*NV*copy*memory*indirect

引数:

  * `supported_queues::QueueFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCopyMemoryIndirectPropertiesNV.html)

```julia
_PhysicalDeviceCopyMemoryIndirectPropertiesNV(
    supported_queues::Vulkan.QueueFlag;
    next
) -> Vulkan._PhysicalDeviceCopyMemoryIndirectPropertiesNV

```
