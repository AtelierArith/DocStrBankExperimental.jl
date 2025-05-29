VkDependencyInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDependencyInfo.html)

```julia
struct _DependencyInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkDependencyInfo`
  * `deps::Vector{Any}`
