High-level wrapper for VkAllocationCallbacks.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAllocationCallbacks.html)

```julia
struct AllocationCallbacks <: Vulkan.HighLevelStruct
```

  * `user_data::Ptr{Nothing}`
  * `pfn_allocation::Union{Ptr{Nothing}, Base.CFunction}`
  * `pfn_reallocation::Union{Ptr{Nothing}, Base.CFunction}`
  * `pfn_free::Union{Ptr{Nothing}, Base.CFunction}`
  * `pfn_internal_allocation::Union{Ptr{Nothing}, Base.CFunction}`
  * `pfn_internal_free::Union{Ptr{Nothing}, Base.CFunction}`
