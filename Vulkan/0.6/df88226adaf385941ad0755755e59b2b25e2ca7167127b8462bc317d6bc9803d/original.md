Extension: VK_NV_ray_tracing

Arguments:

  * `compacted_size::UInt64`
  * `info::_AccelerationStructureInfoNV`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoNV.html)

```julia
_AccelerationStructureCreateInfoNV(
    compacted_size::Integer,
    info::Vulkan._AccelerationStructureInfoNV;
    next
) -> Vulkan._AccelerationStructureCreateInfoNV

```
