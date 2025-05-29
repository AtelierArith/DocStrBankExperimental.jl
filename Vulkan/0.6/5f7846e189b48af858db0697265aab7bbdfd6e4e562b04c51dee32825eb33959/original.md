Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEnumerateDeviceLayerProperties.html)

```julia
_enumerate_device_layer_properties(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan._LayerProperties}, Vulkan.VulkanError}

```
