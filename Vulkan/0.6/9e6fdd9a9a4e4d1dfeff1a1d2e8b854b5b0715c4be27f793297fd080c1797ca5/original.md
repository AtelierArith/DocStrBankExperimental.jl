High-level wrapper for VkTimelineSemaphoreSubmitInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTimelineSemaphoreSubmitInfo.html)

```julia
struct TimelineSemaphoreSubmitInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `wait_semaphore_values::Union{Ptr{Nothing}, Vector{UInt64}}`
  * `signal_semaphore_values::Union{Ptr{Nothing}, Vector{UInt64}}`
