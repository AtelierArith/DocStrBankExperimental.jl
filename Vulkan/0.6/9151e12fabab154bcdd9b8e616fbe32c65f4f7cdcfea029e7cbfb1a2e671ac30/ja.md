引数:

  * `queue_family_properties::_QueueFamilyProperties`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyProperties2.html)

```julia
_QueueFamilyProperties2(
    queue_family_properties::Vulkan._QueueFamilyProperties;
    next
) -> Vulkan._QueueFamilyProperties2

```
