Arguments:

  * `device::Device`
  * `buffer::Buffer`
  * `format::Format`
  * `offset::UInt64`
  * `range::UInt64`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateBufferView.html)

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
