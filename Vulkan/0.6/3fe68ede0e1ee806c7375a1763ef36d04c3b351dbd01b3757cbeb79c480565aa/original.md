Extension: VK_NV_ray_tracing

Arguments:

  * `compacted_size::UInt64`
  * `info::AccelerationStructureInfoNV`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoNV.html)

```julia
AccelerationStructureCreateInfoNV(
    compacted_size::Integer,
    info::Vulkan.AccelerationStructureInfoNV;
    next
) -> Vulkan.AccelerationStructureCreateInfoNV

```
