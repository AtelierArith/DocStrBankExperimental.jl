Extension: VK_EXT_astc_decode_mode

Arguments:

  * `decode_mode::Format`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewASTCDecodeModeEXT.html)

```julia
_ImageViewASTCDecodeModeEXT(
    decode_mode::Vulkan.Format;
    next
) -> Vulkan._ImageViewASTCDecodeModeEXT

```
