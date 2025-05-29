Extension: VK_KHR_pipeline_library

Arguments:

  * `libraries::Vector{Pipeline}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineLibraryCreateInfoKHR.html)

```julia
_PipelineLibraryCreateInfoKHR(
    libraries::AbstractArray;
    next
) -> Vulkan._PipelineLibraryCreateInfoKHR

```
