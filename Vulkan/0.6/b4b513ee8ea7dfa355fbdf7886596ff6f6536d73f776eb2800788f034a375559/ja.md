拡張: VK*EXT*texel*buffer*alignment

引数:

  * `texel_buffer_alignment::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceTexelBufferAlignmentFeaturesEXT.html)

```julia
_PhysicalDeviceTexelBufferAlignmentFeaturesEXT(
    texel_buffer_alignment::Bool;
    next
) -> Vulkan._PhysicalDeviceTexelBufferAlignmentFeaturesEXT

```
