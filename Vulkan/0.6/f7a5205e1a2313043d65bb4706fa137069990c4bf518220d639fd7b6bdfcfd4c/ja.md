引数:

  * `queue_family_index::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::CommandPoolCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandPoolCreateInfo.html)

```julia
CommandPoolCreateInfo(
    queue_family_index::Integer;
    next,
    flags
) -> Vulkan.CommandPoolCreateInfo

```
