Extension: VK_EXT_opacity_micromap

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

Arguments:

  * `device::Device`
  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::MicromapTypeEXT`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `create_flags::MicromapCreateFlagEXT`: defaults to `0`
  * `device_address::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateMicromapEXT.html)

```julia
_create_micromap_ext(
    device,
    buffer,
    offset::Integer,
    size::Integer,
    type::Vulkan.MicromapTypeEXT;
    allocator,
    next,
    create_flags,
    device_address
) -> ResultTypes.Result{Vulkan.MicromapEXT, Vulkan.VulkanError}

```
