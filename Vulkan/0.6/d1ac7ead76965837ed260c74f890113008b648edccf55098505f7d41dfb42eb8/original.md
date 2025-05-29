Arguments:

  * `next::Any`: defaults to `C_NULL`
  * `flags::CommandBufferUsageFlag`: defaults to `0`
  * `inheritance_info::CommandBufferInheritanceInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferBeginInfo.html)

```julia
CommandBufferBeginInfo(
;
    next,
    flags,
    inheritance_info
) -> Vulkan.CommandBufferBeginInfo

```
