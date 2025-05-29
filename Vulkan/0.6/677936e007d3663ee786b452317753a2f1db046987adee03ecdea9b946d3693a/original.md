Arguments:

  * `max_per_set_descriptors::UInt32`
  * `max_memory_allocation_size::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMaintenance3Properties.html)

```julia
_PhysicalDeviceMaintenance3Properties(
    max_per_set_descriptors::Integer,
    max_memory_allocation_size::Integer;
    next
) -> Vulkan._PhysicalDeviceMaintenance3Properties

```
