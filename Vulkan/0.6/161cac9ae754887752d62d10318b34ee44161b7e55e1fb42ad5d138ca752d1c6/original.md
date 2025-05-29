Extension: VK_EXT_descriptor_buffer

Arguments:

  * `device::Device`
  * `descriptor_info::_DescriptorGetInfoEXT`
  * `data_size::UInt`
  * `descriptor::Ptr{Cvoid}` (must be a valid pointer with `data_size` bytes)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDescriptorEXT.html)

```julia
_get_descriptor_ext(
    device,
    descriptor_info::Vulkan._DescriptorGetInfoEXT,
    data_size::Integer,
    descriptor::Ptr{Nothing}
)

```
