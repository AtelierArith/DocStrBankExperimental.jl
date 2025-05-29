拡張: VK*EXT*descriptor_buffer

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `acceleration_structure::AccelerationStructureKHR`: デフォルトは `C_NULL`
  * `acceleration_structure_nv::AccelerationStructureNV`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCaptureDescriptorDataInfoEXT.html)

```julia
_AccelerationStructureCaptureDescriptorDataInfoEXT(
;
    next,
    acceleration_structure,
    acceleration_structure_nv
) -> Vulkan._AccelerationStructureCaptureDescriptorDataInfoEXT

```
