Extension: VK_NV_optical_flow

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `device::Device`
  * `session::OpticalFlowSessionNV`
  * `binding_point::OpticalFlowSessionBindingPointNV`
  * `layout::ImageLayout`
  * `view::ImageView`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBindOpticalFlowSessionImageNV.html)

```julia
bind_optical_flow_session_image_nv(
    device,
    session,
    binding_point::Vulkan.OpticalFlowSessionBindingPointNV,
    layout::Vulkan.ImageLayout;
    view
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
