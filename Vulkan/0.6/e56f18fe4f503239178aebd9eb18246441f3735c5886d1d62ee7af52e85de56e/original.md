Arguments:

  * `pfn_allocation::FunctionPtr`
  * `pfn_reallocation::FunctionPtr`
  * `pfn_free::FunctionPtr`
  * `user_data::Ptr{Cvoid}`: defaults to `C_NULL`
  * `pfn_internal_allocation::FunctionPtr`: defaults to `0`
  * `pfn_internal_free::FunctionPtr`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAllocationCallbacks.html)

```julia
_AllocationCallbacks(
    pfn_allocation::Union{Ptr{Nothing}, Base.CFunction},
    pfn_reallocation::Union{Ptr{Nothing}, Base.CFunction},
    pfn_free::Union{Ptr{Nothing}, Base.CFunction};
    user_data,
    pfn_internal_allocation,
    pfn_internal_free
) -> Vulkan._AllocationCallbacks

```
