Extension: VK_EXT_graphics_pipeline_library

Arguments:

  * `flags::GraphicsPipelineLibraryFlagEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineLibraryCreateInfoEXT.html)

```julia
_GraphicsPipelineLibraryCreateInfoEXT(
    flags::Vulkan.GraphicsPipelineLibraryFlagEXT;
    next
) -> Vulkan._GraphicsPipelineLibraryCreateInfoEXT

```
