引数:

  * `offset::UInt64`
  * `range::UInt64`
  * `buffer::Buffer`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorBufferInfo.html)

```julia
_DescriptorBufferInfo(
    offset::Integer,
    range::Integer;
    buffer
) -> Vulkan._DescriptorBufferInfo

```
