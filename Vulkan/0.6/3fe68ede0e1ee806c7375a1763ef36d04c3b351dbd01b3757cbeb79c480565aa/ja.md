拡張: VK*NV*ray_tracing

引数:

  * `compacted_size::UInt64`
  * `info::AccelerationStructureInfoNV`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoNV.html)

```julia
AccelerationStructureCreateInfoNV(
    compacted_size::Integer,
    info::Vulkan.AccelerationStructureInfoNV;
    next
) -> Vulkan.AccelerationStructureCreateInfoNV

```
