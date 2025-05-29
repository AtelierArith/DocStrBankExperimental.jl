拡張機能: VK*NV*optical_flow

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `create_info::OpticalFlowSessionCreateInfoNV`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateOpticalFlowSessionNV.html)

```julia
create_optical_flow_session_nv(
    device,
    create_info::Vulkan.OpticalFlowSessionCreateInfoNV;
    allocator
) -> ResultTypes.Result{Vulkan.OpticalFlowSessionNV, Vulkan.VulkanError}

```
