Arguments:

  * `offset::UInt64`
  * `range::UInt64`
  * `buffer::Buffer`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorBufferInfo.html)

```julia
DescriptorBufferInfo(
    offset::Integer,
    range::Integer;
    buffer
) -> Vulkan.DescriptorBufferInfo

```
