Extension: VK_NV_coverage_reduction_mode

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSupportedFramebufferMixedSamplesCombinationsNV.html)

```julia
_get_physical_device_supported_framebuffer_mixed_samples_combinations_nv(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan._FramebufferMixedSamplesCombinationNV}, Vulkan.VulkanError}

```
