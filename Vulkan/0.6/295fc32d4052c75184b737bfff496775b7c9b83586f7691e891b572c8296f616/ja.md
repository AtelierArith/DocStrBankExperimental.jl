拡張: VK*KHR*pipeline*executable*properties

引数:

  * `stages::ShaderStageFlag`
  * `name::String`
  * `description::String`
  * `subgroup_size::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutablePropertiesKHR.html)

```julia
PipelineExecutablePropertiesKHR(
    stages::Vulkan.ShaderStageFlag,
    name::AbstractString,
    description::AbstractString,
    subgroup_size::Integer;
    next
) -> Vulkan.PipelineExecutablePropertiesKHR

```
