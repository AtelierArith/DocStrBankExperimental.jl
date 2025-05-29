Extension: VK_NV_optical_flow

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `device::Device`
  * `create_info::OpticalFlowSessionCreateInfoNV`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateOpticalFlowSessionNV.html)

```julia
create_optical_flow_session_nv(
    device,
    create_info::Vulkan.OpticalFlowSessionCreateInfoNV;
    allocator
) -> ResultTypes.Result{Vulkan.OpticalFlowSessionNV, Vulkan.VulkanError}

```
