Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::CommandBufferUsageFlag`: defaults to `0`
  * `inheritance_info::_CommandBufferInheritanceInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferBeginInfo.html)

```julia
_CommandBufferBeginInfo(
;
    next,
    flags,
    inheritance_info
) -> Vulkan._CommandBufferBeginInfo

```
