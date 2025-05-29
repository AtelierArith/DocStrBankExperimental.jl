Arguments:

  * `device::Device`
  * `object_type::ObjectType`
  * `object_handle::UInt64`
  * `private_data_slot::PrivateDataSlot`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPrivateData.html)

```julia
get_private_data(
    device,
    object_type::Vulkan.ObjectType,
    object_handle::Integer,
    private_data_slot
) -> UInt64

```
