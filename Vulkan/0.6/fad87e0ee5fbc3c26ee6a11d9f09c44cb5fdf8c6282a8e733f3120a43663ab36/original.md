Extension: VK_KHR_pipeline_executable_properties

Arguments:

  * `stages::ShaderStageFlag`
  * `name::String`
  * `description::String`
  * `subgroup_size::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutablePropertiesKHR.html)

```julia
_PipelineExecutablePropertiesKHR(
    stages::Vulkan.ShaderStageFlag,
    name::AbstractString,
    description::AbstractString,
    subgroup_size::Integer;
    next
)

```
