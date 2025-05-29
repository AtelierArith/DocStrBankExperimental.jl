拡張: VK*EXT*opacity_micromap

引数:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::MicromapTypeEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `create_flags::MicromapCreateFlagEXT`: デフォルトは `0`
  * `device_address::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapCreateInfoEXT.html)

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
