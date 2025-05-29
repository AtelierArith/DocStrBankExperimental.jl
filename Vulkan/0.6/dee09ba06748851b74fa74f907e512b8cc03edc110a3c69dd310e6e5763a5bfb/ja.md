VkImportFenceFdInfoKHRの高レベルラッパー。

拡張: VK*KHR*external*fence*fd

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportFenceFdInfoKHR.html)

```julia
struct ImportFenceFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `fence::Vulkan.Fence`
  * `flags::Vulkan.FenceImportFlag`
  * `handle_type::Vulkan.ExternalFenceHandleTypeFlag`
  * `fd::Int64`
