Arguments:

  * `contents::SubpassContents`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassBeginInfo.html)

```julia
_SubpassBeginInfo(
    contents::Vulkan.SubpassContents;
    next
) -> Vulkan._SubpassBeginInfo

```
