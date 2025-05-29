拡張: VK*EXT*opacity_micromap

引数:

  * `device::Device`
  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::MicromapTypeEXT`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `create_flags::MicromapCreateFlagEXT`: デフォルトは `0`
  * `device_address::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateMicromapEXT.html)

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
