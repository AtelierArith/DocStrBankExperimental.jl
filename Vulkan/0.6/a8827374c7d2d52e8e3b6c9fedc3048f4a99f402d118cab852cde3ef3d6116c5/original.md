Extension: VK_EXT_conditional_rendering

Arguments:

  * `buffer::Buffer`
  * `offset::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::ConditionalRenderingFlagEXT`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkConditionalRenderingBeginInfoEXT.html)

```julia
_ConditionalRenderingBeginInfoEXT(
    buffer,
    offset::Integer;
    next,
    flags
) -> Vulkan._ConditionalRenderingBeginInfoEXT

```
