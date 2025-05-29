拡張機能: VK*NV*ray_tracing

引数:

  * `device::Device`
  * `compacted_size::UInt64`
  * `info::AccelerationStructureInfoNV`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureNV.html)

```julia
AccelerationStructureNV(
    device,
    compacted_size::Integer,
    info::Vulkan.AccelerationStructureInfoNV;
    allocator,
    next
) -> Vulkan.AccelerationStructureNV

```
