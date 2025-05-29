拡張: VK*EXT*debug_report

引数:

  * `instance::Instance`
  * `callback::DebugReportCallbackEXT` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDebugReportCallbackEXT.html)

```julia
destroy_debug_report_callback_ext(
    instance,
    callback;
    allocator
)

```
