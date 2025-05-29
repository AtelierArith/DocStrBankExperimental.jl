戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEnumerateDeviceLayerProperties.html)

```julia
enumerate_device_layer_properties(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.LayerProperties}, Vulkan.VulkanError}

```
