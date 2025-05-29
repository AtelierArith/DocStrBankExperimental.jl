Extension: VK_KHR_pipeline_executable_properties

Arguments:

  * `pipeline::Pipeline`
  * `executable_index::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableInfoKHR.html)

```julia
_PipelineExecutableInfoKHR(
    pipeline,
    executable_index::Integer;
    next
) -> Vulkan._PipelineExecutableInfoKHR

```
