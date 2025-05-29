Extension: VK_EXT_image_compression_control

Arguments:

  * `flags::ImageCompressionFlagEXT`
  * `fixed_rate_flags::Vector{ImageCompressionFixedRateFlagEXT}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCompressionControlEXT.html)

```julia
_ImageCompressionControlEXT(
    flags::Vulkan.ImageCompressionFlagEXT,
    fixed_rate_flags::AbstractArray;
    next
) -> Vulkan._ImageCompressionControlEXT

```
