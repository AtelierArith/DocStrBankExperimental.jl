拡張機能: VK*NV*optical_flow

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `create_info::_OpticalFlowSessionCreateInfoNV`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateOpticalFlowSessionNV.html)

```julia
_create_optical_flow_session_nv(
    device,
    create_info::Vulkan._OpticalFlowSessionCreateInfoNV;
    allocator
) -> ResultTypes.Result{Vulkan.OpticalFlowSessionNV, Vulkan.VulkanError}

```
