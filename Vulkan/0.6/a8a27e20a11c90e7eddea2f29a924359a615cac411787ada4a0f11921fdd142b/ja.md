VkDirectDriverLoadingInfoLUNARGの高レベルラッパー。

拡張: VK*LUNARG*direct*driver*loading

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDirectDriverLoadingInfoLUNARG.html)

```julia
struct DirectDriverLoadingInfoLUNARG <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `pfn_get_instance_proc_addr::Union{Ptr{Nothing}, Base.CFunction}`
