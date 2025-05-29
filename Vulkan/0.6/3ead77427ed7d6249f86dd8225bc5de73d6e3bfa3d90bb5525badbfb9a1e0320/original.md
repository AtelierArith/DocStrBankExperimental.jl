Extension: VK_EXT_descriptor_buffer

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `acceleration_structure::AccelerationStructureKHR`: defaults to `C_NULL`
  * `acceleration_structure_nv::AccelerationStructureNV`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCaptureDescriptorDataInfoEXT.html)

```julia
_AccelerationStructureCaptureDescriptorDataInfoEXT(
;
    next,
    acceleration_structure,
    acceleration_structure_nv
) -> Vulkan._AccelerationStructureCaptureDescriptorDataInfoEXT

```
