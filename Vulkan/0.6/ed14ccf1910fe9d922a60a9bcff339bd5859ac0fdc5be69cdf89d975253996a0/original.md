Extension: VK_KHR_pipeline_executable_properties

Arguments:

  * `name::String`
  * `description::String`
  * `format::PipelineExecutableStatisticFormatKHR`
  * `value::PipelineExecutableStatisticValueKHR`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableStatisticKHR.html)

```julia
PipelineExecutableStatisticKHR(
    name::AbstractString,
    description::AbstractString,
    format::Vulkan.PipelineExecutableStatisticFormatKHR,
    value::Vulkan.PipelineExecutableStatisticValueKHR;
    next
) -> Vulkan.PipelineExecutableStatisticKHR

```
