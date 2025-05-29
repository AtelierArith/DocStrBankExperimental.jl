Arguments:

  * `binding::UInt32`
  * `descriptor_type::DescriptorType`
  * `stage_flags::ShaderStageFlag`
  * `descriptor_count::UInt32`: defaults to `0`
  * `immutable_samplers::Vector{Sampler}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutBinding.html)

```julia
_DescriptorSetLayoutBinding(
    binding::Integer,
    descriptor_type::Vulkan.DescriptorType,
    stage_flags::Vulkan.ShaderStageFlag;
    descriptor_count,
    immutable_samplers
) -> Vulkan._DescriptorSetLayoutBinding

```
