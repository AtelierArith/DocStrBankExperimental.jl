High-level wrapper for VkSubmitInfo2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubmitInfo2.html)

```julia
struct SubmitInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.SubmitFlag`
  * `wait_semaphore_infos::Vector{Vulkan.SemaphoreSubmitInfo}`
  * `command_buffer_infos::Vector{Vulkan.CommandBufferSubmitInfo}`
  * `signal_semaphore_infos::Vector{Vulkan.SemaphoreSubmitInfo}`
