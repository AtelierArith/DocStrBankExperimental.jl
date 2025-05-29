拡張: VK*NV*ray_tracing

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `acceleration_structure::AccelerationStructureNV`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}` (必ず `data_size` バイトの有効なポインタである必要があります)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetAccelerationStructureHandleNV.html)

```julia
_get_acceleration_structure_handle_nv(
    device,
    acceleration_structure,
    data_size::Integer,
    data::Ptr{Nothing}
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
