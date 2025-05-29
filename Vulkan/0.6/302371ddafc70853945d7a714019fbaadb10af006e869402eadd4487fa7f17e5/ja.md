拡張: VK*VALVE*descriptor*set*host_mapping

引数:

  * `descriptor_set_layout::DescriptorSetLayout`
  * `binding::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetBindingReferenceVALVE.html)

```julia
DescriptorSetBindingReferenceVALVE(
    descriptor_set_layout::Vulkan.DescriptorSetLayout,
    binding::Integer;
    next
) -> Vulkan.DescriptorSetBindingReferenceVALVE

```
