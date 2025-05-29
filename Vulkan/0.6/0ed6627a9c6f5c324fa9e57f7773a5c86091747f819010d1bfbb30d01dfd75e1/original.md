Extension: VK_KHR_pipeline_executable_properties

Arguments:

  * `name::String`
  * `description::String`
  * `format::PipelineExecutableStatisticFormatKHR`
  * `value::_PipelineExecutableStatisticValueKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableStatisticKHR.html)

```julia
_PipelineExecutableStatisticKHR(
    name::AbstractString,
    description::AbstractString,
    format::Vulkan.PipelineExecutableStatisticFormatKHR,
    value::Vulkan._PipelineExecutableStatisticValueKHR;
    next
)

```
