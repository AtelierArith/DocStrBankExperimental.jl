拡張機能: VK*INTEL*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `marker_info::_PerformanceMarkerInfoINTEL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetPerformanceMarkerINTEL.html)

```julia
_cmd_set_performance_marker_intel(
    command_buffer,
    marker_info::Vulkan._PerformanceMarkerInfoINTEL
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
