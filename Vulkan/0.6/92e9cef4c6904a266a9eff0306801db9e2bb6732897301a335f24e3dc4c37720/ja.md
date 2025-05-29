拡張: VK*VALVE*descriptor*set*host_mapping

引数:

  * `descriptor_offset::UInt`
  * `descriptor_size::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutHostMappingInfoVALVE.html)

```julia
DescriptorSetLayoutHostMappingInfoVALVE(
    descriptor_offset::Integer,
    descriptor_size::Integer;
    next
) -> Vulkan.DescriptorSetLayoutHostMappingInfoVALVE

```
