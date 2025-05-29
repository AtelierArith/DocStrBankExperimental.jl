拡張: VK*NV*ray_tracing

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `compacted_size::UInt64`
  * `info::_AccelerationStructureInfoNV`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureNV.html)

```julia
_create_acceleration_structure_nv(
    device,
    compacted_size::Integer,
    info::Vulkan._AccelerationStructureInfoNV;
    allocator,
    next
) -> ResultTypes.Result{Vulkan.AccelerationStructureNV, Vulkan.VulkanError}

```
