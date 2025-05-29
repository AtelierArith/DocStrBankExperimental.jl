拡張: VK*EXT*debug_report

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `instance::Instance`
  * `pfn_callback::FunctionPtr`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::DebugReportFlagEXT`: デフォルトは `0`
  * `user_data::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugReportCallbackEXT.html)

```julia
create_debug_report_callback_ext(
    instance,
    pfn_callback::Union{Ptr{Nothing}, Base.CFunction};
    allocator,
    next,
    flags,
    user_data
) -> ResultTypes.Result{Vulkan.DebugReportCallbackEXT, Vulkan.VulkanError}

```
