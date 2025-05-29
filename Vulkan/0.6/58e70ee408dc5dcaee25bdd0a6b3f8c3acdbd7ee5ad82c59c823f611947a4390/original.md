Extension: VK_KHR_pipeline_library

Arguments:

  * `libraries::Vector{Pipeline}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineLibraryCreateInfoKHR.html)

```julia
PipelineLibraryCreateInfoKHR(
    libraries::AbstractArray;
    next
) -> Vulkan.PipelineLibraryCreateInfoKHR

```
