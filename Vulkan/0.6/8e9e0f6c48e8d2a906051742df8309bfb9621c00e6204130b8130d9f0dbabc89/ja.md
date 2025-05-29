拡張機能: VK*INTEL*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `override_info::_PerformanceOverrideInfoINTEL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetPerformanceOverrideINTEL.html)

```julia
_cmd_set_performance_override_intel(
    command_buffer,
    override_info::Vulkan._PerformanceOverrideInfoINTEL
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
