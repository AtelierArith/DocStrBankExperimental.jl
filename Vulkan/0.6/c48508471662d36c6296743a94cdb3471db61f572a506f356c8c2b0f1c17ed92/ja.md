拡張: VK*EXT*conditional_rendering

引数:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::ConditionalRenderingFlagEXT`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkConditionalRenderingBeginInfoEXT.html)

```julia
ConditionalRenderingBeginInfoEXT(
    buffer::Vulkan.Buffer,
    offset::Integer;
    next,
    flags
) -> Vulkan.ConditionalRenderingBeginInfoEXT

```
