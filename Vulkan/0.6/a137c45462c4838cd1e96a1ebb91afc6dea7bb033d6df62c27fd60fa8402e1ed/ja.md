拡張機能: VK*KHR*video_queue

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `create_info::_VideoSessionParametersCreateInfoKHR`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionParametersKHR.html)

```julia
_create_video_session_parameters_khr(
    device,
    create_info::Vulkan._VideoSessionParametersCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.VideoSessionParametersKHR, Vulkan.VulkanError}

```
