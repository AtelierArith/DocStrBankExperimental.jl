Extension: VK_EXT_debug_report

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `instance::Instance`
  * `pfn_callback::FunctionPtr`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::DebugReportFlagEXT`: defaults to `0`
  * `user_data::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugReportCallbackEXT.html)

```julia
_create_debug_report_callback_ext(
    instance,
    pfn_callback::Union{Ptr{Nothing}, Base.CFunction};
    allocator,
    next,
    flags,
    user_data
) -> ResultTypes.Result{Vulkan.DebugReportCallbackEXT, Vulkan.VulkanError}

```
