Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `object_type::ObjectType`
  * `object_handle::UInt64`
  * `private_data_slot::PrivateDataSlot`
  * `data::UInt64`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSetPrivateData.html)

```julia
set_private_data(
    device,
    object_type::Vulkan.ObjectType,
    object_handle::Integer,
    private_data_slot,
    data::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
