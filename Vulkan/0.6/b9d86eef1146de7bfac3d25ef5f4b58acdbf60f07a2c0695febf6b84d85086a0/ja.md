拡張: VK*EXT*graphics*pipeline*library

引数:

  * `flags::GraphicsPipelineLibraryFlagEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineLibraryCreateInfoEXT.html)

```julia
_GraphicsPipelineLibraryCreateInfoEXT(
    flags::Vulkan.GraphicsPipelineLibraryFlagEXT;
    next
) -> Vulkan._GraphicsPipelineLibraryCreateInfoEXT

```
