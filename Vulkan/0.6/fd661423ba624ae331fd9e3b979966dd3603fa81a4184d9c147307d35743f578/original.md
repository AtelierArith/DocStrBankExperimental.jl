Arguments:

  * `queue_family_index::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::CommandPoolCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandPoolCreateInfo.html)

```julia
_CommandPoolCreateInfo(
    queue_family_index::Integer;
    next,
    flags
) -> Vulkan._CommandPoolCreateInfo

```
