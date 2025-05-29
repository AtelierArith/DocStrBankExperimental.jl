Extension: VK_EXT_opacity_micromap

Arguments:

  * `device::Device`
  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::MicromapTypeEXT`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `create_flags::MicromapCreateFlagEXT`: defaults to `0`
  * `device_address::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateMicromapEXT.html)

```julia
MicromapEXT(
    device,
    buffer,
    offset::Integer,
    size::Integer,
    type::Vulkan.MicromapTypeEXT;
    allocator,
    next,
    create_flags,
    device_address
) -> Vulkan.MicromapEXT

```
