拡張: VK*VALVE*descriptor*set*host_mapping

引数:

  * `descriptor_set_layout::DescriptorSetLayout`
  * `binding::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetBindingReferenceVALVE.html)

```julia
_DescriptorSetBindingReferenceVALVE(
    descriptor_set_layout,
    binding::Integer;
    next
) -> Vulkan._DescriptorSetBindingReferenceVALVE

```
