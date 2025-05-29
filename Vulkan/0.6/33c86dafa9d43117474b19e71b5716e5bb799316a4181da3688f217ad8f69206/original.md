Arguments:

  * `max_variable_descriptor_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetVariableDescriptorCountLayoutSupport.html)

```julia
_DescriptorSetVariableDescriptorCountLayoutSupport(
    max_variable_descriptor_count::Integer;
    next
) -> Vulkan._DescriptorSetVariableDescriptorCountLayoutSupport

```
