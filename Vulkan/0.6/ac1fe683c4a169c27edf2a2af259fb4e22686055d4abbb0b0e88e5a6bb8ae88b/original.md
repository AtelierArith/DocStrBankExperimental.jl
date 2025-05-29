Extension: VK_KHR_pipeline_executable_properties

Arguments:

  * `pipeline::Pipeline`
  * `executable_index::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableInfoKHR.html)

```julia
PipelineExecutableInfoKHR(
    pipeline::Vulkan.Pipeline,
    executable_index::Integer;
    next
) -> Vulkan.PipelineExecutableInfoKHR

```
