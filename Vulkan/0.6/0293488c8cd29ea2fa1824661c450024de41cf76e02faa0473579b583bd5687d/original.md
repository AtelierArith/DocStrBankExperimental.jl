Extension: VK_HUAWEI_subpass_shading

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `device::Device`
  * `renderpass::RenderPass`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceSubpassShadingMaxWorkgroupSizeHUAWEI.html)

```julia
_get_device_subpass_shading_max_workgroup_size_huawei(
    device,
    renderpass
) -> ResultTypes.Result{Vulkan._Extent2D, Vulkan.VulkanError}

```
