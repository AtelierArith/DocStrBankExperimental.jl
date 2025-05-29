引数:

  * `buffer::Buffer`
  * `format::Format`
  * `offset::UInt64`
  * `range::UInt64`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferViewCreateInfo.html)

```julia
BufferViewCreateInfo(
    buffer::Vulkan.Buffer,
    format::Vulkan.Format,
    offset::Integer,
    range::Integer;
    next,
    flags
) -> Vulkan.BufferViewCreateInfo

```
