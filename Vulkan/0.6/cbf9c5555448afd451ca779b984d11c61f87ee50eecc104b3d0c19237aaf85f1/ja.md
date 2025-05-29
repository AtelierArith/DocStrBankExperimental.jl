引数:

  * `device::Device`
  * `buffer::Buffer`
  * `format::Format`
  * `offset::UInt64`
  * `range::UInt64`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateBufferView.html)

```julia
BufferView(
    device,
    buffer,
    format::Vulkan.Format,
    offset::Integer,
    range::Integer;
    allocator,
    next,
    flags
) -> Vulkan.BufferView

```
