Extension: VK_EXT_color_write_enable

Arguments:

  * `color_write_enables::Vector{Bool}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorWriteCreateInfoEXT.html)

```julia
_PipelineColorWriteCreateInfoEXT(
    color_write_enables::AbstractArray;
    next
) -> Vulkan._PipelineColorWriteCreateInfoEXT

```
