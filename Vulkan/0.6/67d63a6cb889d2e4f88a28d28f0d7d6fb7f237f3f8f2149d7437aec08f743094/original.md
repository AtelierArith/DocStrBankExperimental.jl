High-level wrapper for VkFenceGetFdInfoKHR.

Extension: VK_KHR_external_fence_fd

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFenceGetFdInfoKHR.html)

```julia
struct FenceGetFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `fence::Vulkan.Fence`
  * `handle_type::Vulkan.ExternalFenceHandleTypeFlag`
