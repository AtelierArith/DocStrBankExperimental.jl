拡張: VK*KHR*video_queue

引数:

  * `query_result_status_support::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyQueryResultStatusPropertiesKHR.html)

```julia
_QueueFamilyQueryResultStatusPropertiesKHR(
    query_result_status_support::Bool;
    next
) -> Vulkan._QueueFamilyQueryResultStatusPropertiesKHR

```
