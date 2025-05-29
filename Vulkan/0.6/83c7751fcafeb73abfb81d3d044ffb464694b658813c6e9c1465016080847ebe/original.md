Extension: VK_EXT_debug_report

Arguments:

  * `instance::Instance`
  * `callback::DebugReportCallbackEXT` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDebugReportCallbackEXT.html)

```julia
destroy_debug_report_callback_ext(
    instance,
    callback;
    allocator
)

```
