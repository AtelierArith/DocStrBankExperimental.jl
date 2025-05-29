拡張: VK*KHR*acceleration_structure

引数:

  * `device::Device`
  * `acceleration_structure::AccelerationStructureKHR` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyAccelerationStructureKHR.html)

```julia
destroy_acceleration_structure_khr(
    device,
    acceleration_structure;
    allocator
)

```
