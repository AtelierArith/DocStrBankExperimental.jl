Arguments:

  * `device::Device`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::EventCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateEvent.html)

```julia
Event(device; allocator, next, flags) -> Vulkan.Event

```
