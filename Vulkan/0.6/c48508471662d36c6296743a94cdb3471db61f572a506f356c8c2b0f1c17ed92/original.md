Extension: VK_EXT_conditional_rendering

Arguments:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `next::Any`: defaults to `C_NULL`
  * `flags::ConditionalRenderingFlagEXT`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkConditionalRenderingBeginInfoEXT.html)

```julia
ConditionalRenderingBeginInfoEXT(
    buffer::Vulkan.Buffer,
    offset::Integer;
    next,
    flags
) -> Vulkan.ConditionalRenderingBeginInfoEXT

```
