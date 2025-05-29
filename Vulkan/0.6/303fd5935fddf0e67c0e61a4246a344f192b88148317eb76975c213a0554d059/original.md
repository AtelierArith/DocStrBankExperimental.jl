Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

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
create_buffer_view(
    device,
    buffer,
    format::Vulkan.Format,
    offset::Integer,
    range::Integer;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.BufferView, Vulkan.VulkanError}

```
