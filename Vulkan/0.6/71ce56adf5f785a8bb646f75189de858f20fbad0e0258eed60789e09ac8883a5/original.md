Extension: VK_VALVE_descriptor_set_host_mapping

Arguments:

  * `descriptor_set_layout::DescriptorSetLayout`
  * `binding::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetBindingReferenceVALVE.html)

```julia
_DescriptorSetBindingReferenceVALVE(
    descriptor_set_layout,
    binding::Integer;
    next
) -> Vulkan._DescriptorSetBindingReferenceVALVE

```
