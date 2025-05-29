拡張: VK*NV*optical_flow

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `session::OpticalFlowSessionNV`
  * `binding_point::OpticalFlowSessionBindingPointNV`
  * `layout::ImageLayout`
  * `view::ImageView`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBindOpticalFlowSessionImageNV.html)

```julia
_bind_optical_flow_session_image_nv(
    device,
    session,
    binding_point::Vulkan.OpticalFlowSessionBindingPointNV,
    layout::Vulkan.ImageLayout;
    view
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
