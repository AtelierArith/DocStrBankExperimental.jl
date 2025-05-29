拡張: VK*EXT*conditional_rendering

引数:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::ConditionalRenderingFlagEXT`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkConditionalRenderingBeginInfoEXT.html)

```julia
_ConditionalRenderingBeginInfoEXT(
    buffer,
    offset::Integer;
    next,
    flags
) -> Vulkan._ConditionalRenderingBeginInfoEXT

```
