拡張: VK*EXT*color*write*enable

引数:

  * `color_write_enables::Vector{Bool}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorWriteCreateInfoEXT.html)

```julia
PipelineColorWriteCreateInfoEXT(
    color_write_enables::AbstractArray;
    next
) -> Vulkan.PipelineColorWriteCreateInfoEXT

```
