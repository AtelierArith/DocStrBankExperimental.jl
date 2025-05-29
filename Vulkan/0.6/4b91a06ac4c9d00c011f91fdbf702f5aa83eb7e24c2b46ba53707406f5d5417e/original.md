Intermediate wrapper for VkVideoSessionParametersCreateInfoKHR.

Extension: VK_KHR_video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionParametersCreateInfoKHR.html)

```julia
struct _VideoSessionParametersCreateInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkVideoSessionParametersCreateInfoKHR`
  * `deps::Vector{Any}`
  * `video_session_parameters_template::Union{Ptr{Nothing}, Vulkan.VideoSessionParametersKHR}`
  * `video_session::Vulkan.VideoSessionKHR`
