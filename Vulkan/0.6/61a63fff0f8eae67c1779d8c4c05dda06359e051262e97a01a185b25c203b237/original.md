Arguments:

  * `buffer::Buffer`
  * `format::Format`
  * `offset::UInt64`
  * `range::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferViewCreateInfo.html)

```julia
_BufferViewCreateInfo(
    buffer,
    format::Vulkan.Format,
    offset::Integer,
    range::Integer;
    next,
    flags
) -> Vulkan._BufferViewCreateInfo

```
