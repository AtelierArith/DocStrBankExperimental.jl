High-level wrapper for VkDirectDriverLoadingInfoLUNARG.

Extension: VK_LUNARG_direct_driver_loading

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDirectDriverLoadingInfoLUNARG.html)

```julia
struct DirectDriverLoadingInfoLUNARG <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `pfn_get_instance_proc_addr::Union{Ptr{Nothing}, Base.CFunction}`
