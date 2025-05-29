引数:

  * `binding::UInt32`
  * `descriptor_type::DescriptorType`
  * `stage_flags::ShaderStageFlag`
  * `descriptor_count::UInt32`: デフォルトは `0`
  * `immutable_samplers::Vector{Sampler}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutBinding.html)

```julia
_DescriptorSetLayoutBinding(
    binding::Integer,
    descriptor_type::Vulkan.DescriptorType,
    stage_flags::Vulkan.ShaderStageFlag;
    descriptor_count,
    immutable_samplers
) -> Vulkan._DescriptorSetLayoutBinding

```
