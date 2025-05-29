Arguments:

  * `device::Device`
  * `flags::UInt32`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePrivateDataSlot.html)

```julia
PrivateDataSlot(
    device,
    flags::Integer;
    allocator,
    next
) -> Vulkan.PrivateDataSlot

```
