拡張: VK*NV*ray_tracing

引数:

  * `device::Device`
  * `acceleration_structure::AccelerationStructureNV` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyAccelerationStructureNV.html)

```julia
destroy_acceleration_structure_nv(
    device,
    acceleration_structure;
    allocator
)

```
