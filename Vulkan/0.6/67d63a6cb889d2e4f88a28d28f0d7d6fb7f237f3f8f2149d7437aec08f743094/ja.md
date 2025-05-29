VkFenceGetFdInfoKHRの高レベルラッパー。

拡張: VK*KHR*external*fence*fd

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFenceGetFdInfoKHR.html)

```julia
struct FenceGetFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `fence::Vulkan.Fence`
  * `handle_type::Vulkan.ExternalFenceHandleTypeFlag`
