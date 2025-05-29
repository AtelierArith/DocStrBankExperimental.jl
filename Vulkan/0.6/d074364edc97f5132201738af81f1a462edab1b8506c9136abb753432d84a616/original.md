Extension: VK_VALVE_descriptor_set_host_mapping

Arguments:

  * `descriptor_offset::UInt`
  * `descriptor_size::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutHostMappingInfoVALVE.html)

```julia
_DescriptorSetLayoutHostMappingInfoVALVE(
    descriptor_offset::Integer,
    descriptor_size::Integer;
    next
) -> Vulkan._DescriptorSetLayoutHostMappingInfoVALVE

```
