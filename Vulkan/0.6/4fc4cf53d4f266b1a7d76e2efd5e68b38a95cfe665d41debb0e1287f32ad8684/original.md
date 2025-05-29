Extension: VK_EXT_debug_report

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `instance::Instance`
  * `create_info::_DebugReportCallbackCreateInfoEXT`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugReportCallbackEXT.html)

```julia
_create_debug_report_callback_ext(
    instance,
    create_info::Vulkan._DebugReportCallbackCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.DebugReportCallbackEXT, Vulkan.VulkanError}

```
