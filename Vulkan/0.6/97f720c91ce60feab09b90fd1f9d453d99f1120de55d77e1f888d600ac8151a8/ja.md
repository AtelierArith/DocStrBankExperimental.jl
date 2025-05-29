拡張: VK*KHR*pipeline_library

引数:

  * `libraries::Vector{Pipeline}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineLibraryCreateInfoKHR.html)

```julia
_PipelineLibraryCreateInfoKHR(
    libraries::AbstractArray;
    next
) -> Vulkan._PipelineLibraryCreateInfoKHR

```
