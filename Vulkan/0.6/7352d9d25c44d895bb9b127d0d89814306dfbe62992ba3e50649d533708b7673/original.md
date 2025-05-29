Extension: VK_EXT_opacity_micromap

Arguments:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::MicromapTypeEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `create_flags::MicromapCreateFlagEXT`: defaults to `0`
  * `device_address::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapCreateInfoEXT.html)

```julia
_MicromapCreateInfoEXT(
    buffer,
    offset::Integer,
    size::Integer,
    type::Vulkan.MicromapTypeEXT;
    next,
    create_flags,
    device_address
) -> Vulkan._MicromapCreateInfoEXT

```
