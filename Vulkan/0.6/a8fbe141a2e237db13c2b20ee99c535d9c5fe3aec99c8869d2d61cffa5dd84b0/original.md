Intermediate wrapper for VkVideoBeginCodingInfoKHR.

Extension: VK_KHR_video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoBeginCodingInfoKHR.html)

```julia
struct _VideoBeginCodingInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkVideoBeginCodingInfoKHR`
  * `deps::Vector{Any}`
  * `video_session::Vulkan.VideoSessionKHR`
  * `video_session_parameters::Union{Ptr{Nothing}, Vulkan.VideoSessionParametersKHR}`
