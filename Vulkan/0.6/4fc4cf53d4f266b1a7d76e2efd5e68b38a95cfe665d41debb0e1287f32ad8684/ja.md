拡張: VK*EXT*debug_report

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `instance::Instance`
  * `create_info::_DebugReportCallbackCreateInfoEXT`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugReportCallbackEXT.html)

```julia
_create_debug_report_callback_ext(
    instance,
    create_info::Vulkan._DebugReportCallbackCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.DebugReportCallbackEXT, Vulkan.VulkanError}

```
