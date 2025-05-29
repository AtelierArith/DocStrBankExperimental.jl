Extension: VK_EXT_descriptor_buffer

Arguments:

  * `device::Device`
  * `descriptor_info::DescriptorGetInfoEXT`
  * `data_size::UInt`
  * `descriptor::Ptr{Cvoid}` (must be a valid pointer with `data_size` bytes)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDescriptorEXT.html)

```julia
get_descriptor_ext(
    device,
    descriptor_info::Vulkan.DescriptorGetInfoEXT,
    data_size::Integer,
    descriptor::Ptr{Nothing}
)

```
