拡張: VK*KHR*pipeline_library

引数:

  * `libraries::Vector{Pipeline}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineLibraryCreateInfoKHR.html)

```julia
PipelineLibraryCreateInfoKHR(
    libraries::AbstractArray;
    next
) -> Vulkan.PipelineLibraryCreateInfoKHR

```
