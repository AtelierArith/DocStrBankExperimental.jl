拡張: VK*EXT*descriptor_buffer

引数:

  * `device::Device`
  * `descriptor_info::DescriptorGetInfoEXT`
  * `data_size::UInt`
  * `descriptor::Ptr{Cvoid}` (必ず `data_size` バイトの有効なポインタである必要があります)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDescriptorEXT.html)

```julia
get_descriptor_ext(
    device,
    descriptor_info::Vulkan.DescriptorGetInfoEXT,
    data_size::Integer,
    descriptor::Ptr{Nothing}
)

```
