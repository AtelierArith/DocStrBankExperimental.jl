拡張: VK*EXT*image*compression*control

引数:

  * `flags::ImageCompressionFlagEXT`
  * `fixed_rate_flags::Vector{ImageCompressionFixedRateFlagEXT}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCompressionControlEXT.html)

```julia
_ImageCompressionControlEXT(
    flags::Vulkan.ImageCompressionFlagEXT,
    fixed_rate_flags::AbstractArray;
    next
) -> Vulkan._ImageCompressionControlEXT

```
