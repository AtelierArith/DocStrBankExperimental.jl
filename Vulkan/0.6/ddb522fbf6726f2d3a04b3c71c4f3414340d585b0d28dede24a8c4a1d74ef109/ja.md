拡張: VK*KHR*acceleration_structure

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `acceleration_structures::Vector{AccelerationStructureKHR}`
  * `query_type::QueryType`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}` (必ず `data_size` バイトの有効なポインタである必要があります)
  * `stride::UInt`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkWriteAccelerationStructuresPropertiesKHR.html)

```julia
write_acceleration_structures_properties_khr(
    device,
    acceleration_structures::AbstractArray,
    query_type::Vulkan.QueryType,
    data_size::Integer,
    data::Ptr{Nothing},
    stride::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
