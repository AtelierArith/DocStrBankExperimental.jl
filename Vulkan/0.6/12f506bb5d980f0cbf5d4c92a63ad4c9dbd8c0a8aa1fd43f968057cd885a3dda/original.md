Intermediate wrapper for VkImportFenceFdInfoKHR.

Extension: VK_KHR_external_fence_fd

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportFenceFdInfoKHR.html)

```julia
struct _ImportFenceFdInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkImportFenceFdInfoKHR`
  * `deps::Vector{Any}`
  * `fence::Vulkan.Fence`
