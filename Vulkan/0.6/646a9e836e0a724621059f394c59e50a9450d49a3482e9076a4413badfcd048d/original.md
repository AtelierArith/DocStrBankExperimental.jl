High-level wrapper for VkSubmitInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubmitInfo.html)

```julia
struct SubmitInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `wait_semaphores::Vector{Vulkan.Semaphore}`
  * `wait_dst_stage_mask::Vector{Vulkan.PipelineStageFlag}`
  * `command_buffers::Vector{Vulkan.CommandBuffer}`
  * `signal_semaphores::Vector{Vulkan.Semaphore}`
