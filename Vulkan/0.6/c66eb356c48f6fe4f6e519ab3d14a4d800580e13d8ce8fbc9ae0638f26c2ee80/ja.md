拡張機能: VK*NV*ray_tracing

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `create_info::AccelerationStructureCreateInfoNV`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureNV.html)

```julia
create_acceleration_structure_nv(
    device,
    create_info::Vulkan.AccelerationStructureCreateInfoNV;
    allocator
) -> ResultTypes.Result{Vulkan.AccelerationStructureNV, Vulkan.VulkanError}

```
