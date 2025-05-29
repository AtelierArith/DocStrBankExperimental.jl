拡張: VK*KHR*video_queue

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `video_session_parameters::VideoSessionParametersKHR`
  * `update_info::_VideoSessionParametersUpdateInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkUpdateVideoSessionParametersKHR.html)

```julia
_update_video_session_parameters_khr(
    device,
    video_session_parameters,
    update_info::Vulkan._VideoSessionParametersUpdateInfoKHR
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
