Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceToolProperties.html)

```julia
get_physical_device_tool_properties(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.PhysicalDeviceToolProperties}, Vulkan.VulkanError}

```
