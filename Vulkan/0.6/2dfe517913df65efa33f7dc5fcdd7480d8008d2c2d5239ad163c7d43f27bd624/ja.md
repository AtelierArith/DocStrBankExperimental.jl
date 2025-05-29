拡張: VK*EXT*descriptor_buffer

引数:

  * `opaque_capture_descriptor_data::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkOpaqueCaptureDescriptorDataCreateInfoEXT.html)

```julia
_OpaqueCaptureDescriptorDataCreateInfoEXT(
    opaque_capture_descriptor_data::Ptr{Nothing};
    next
) -> Vulkan._OpaqueCaptureDescriptorDataCreateInfoEXT

```
