Arguments:

  * `pfn_allocation::FunctionPtr`
  * `pfn_reallocation::FunctionPtr`
  * `pfn_free::FunctionPtr`
  * `user_data::Ptr{Cvoid}`: defaults to `C_NULL`
  * `pfn_internal_allocation::FunctionPtr`: defaults to `C_NULL`
  * `pfn_internal_free::FunctionPtr`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAllocationCallbacks.html)

```julia
AllocationCallbacks(
    pfn_allocation::Union{Ptr{Nothing}, Base.CFunction},
    pfn_reallocation::Union{Ptr{Nothing}, Base.CFunction},
    pfn_free::Union{Ptr{Nothing}, Base.CFunction};
    user_data,
    pfn_internal_allocation,
    pfn_internal_free
) -> Vulkan.AllocationCallbacks

```
