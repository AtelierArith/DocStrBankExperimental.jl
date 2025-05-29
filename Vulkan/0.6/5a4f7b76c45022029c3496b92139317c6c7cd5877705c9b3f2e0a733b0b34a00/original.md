Extension: VK_INTEL_performance_query

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `marker_info::PerformanceMarkerInfoINTEL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetPerformanceMarkerINTEL.html)

```julia
cmd_set_performance_marker_intel(
    command_buffer,
    marker_info::Vulkan.PerformanceMarkerInfoINTEL
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
