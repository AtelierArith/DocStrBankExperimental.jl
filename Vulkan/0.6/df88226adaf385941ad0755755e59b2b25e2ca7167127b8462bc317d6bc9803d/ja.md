拡張: VK*NV*ray_tracing

引数:

  * `compacted_size::UInt64`
  * `info::_AccelerationStructureInfoNV`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoNV.html)

```julia
_AccelerationStructureCreateInfoNV(
    compacted_size::Integer,
    info::Vulkan._AccelerationStructureInfoNV;
    next
) -> Vulkan._AccelerationStructureCreateInfoNV

```
