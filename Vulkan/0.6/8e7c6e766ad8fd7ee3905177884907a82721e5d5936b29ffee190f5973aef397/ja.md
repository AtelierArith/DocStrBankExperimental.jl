VkDirectDriverLoadingListLUNARGの高レベルラッパー。

拡張: VK*LUNARG*direct*driver*loading

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDirectDriverLoadingListLUNARG.html)

```julia
struct DirectDriverLoadingListLUNARG <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `mode::Vulkan.DirectDriverLoadingModeLUNARG`
  * `drivers::Vector{Vulkan.DirectDriverLoadingInfoLUNARG}`
