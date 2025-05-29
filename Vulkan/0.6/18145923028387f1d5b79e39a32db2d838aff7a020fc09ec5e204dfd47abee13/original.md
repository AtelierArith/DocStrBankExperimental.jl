Extension: VK_KHR_video_queue

Arguments:

  * `query_result_status_support::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyQueryResultStatusPropertiesKHR.html)

```julia
_QueueFamilyQueryResultStatusPropertiesKHR(
    query_result_status_support::Bool;
    next
) -> Vulkan._QueueFamilyQueryResultStatusPropertiesKHR

```
