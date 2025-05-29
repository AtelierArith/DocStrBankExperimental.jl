引数:

  * `max_per_set_descriptors::UInt32`
  * `max_memory_allocation_size::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMaintenance3Properties.html)

```julia
_PhysicalDeviceMaintenance3Properties(
    max_per_set_descriptors::Integer,
    max_memory_allocation_size::Integer;
    next
) -> Vulkan._PhysicalDeviceMaintenance3Properties

```
