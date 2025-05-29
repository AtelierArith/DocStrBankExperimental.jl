Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_LAYER_NOT_PRESENT`

Arguments:

  * `physical_device::PhysicalDevice`
  * `layer_name::String`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEnumerateDeviceExtensionProperties.html)

```julia
enumerate_device_extension_properties(
    physical_device;
    layer_name
) -> ResultTypes.Result{Vector{Vulkan.ExtensionProperties}, Vulkan.VulkanError}

```
