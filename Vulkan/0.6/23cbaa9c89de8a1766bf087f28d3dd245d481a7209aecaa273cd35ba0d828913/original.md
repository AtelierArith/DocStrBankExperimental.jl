Extension: VK_EXT_debug_report

Arguments:

  * `instance::Instance`
  * `pfn_callback::FunctionPtr`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::DebugReportFlagEXT`: defaults to `0`
  * `user_data::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugReportCallbackEXT.html)

```julia
DebugReportCallbackEXT(
    instance,
    pfn_callback::Union{Ptr{Nothing}, Base.CFunction};
    allocator,
    next,
    flags,
    user_data
) -> Vulkan.DebugReportCallbackEXT

```
