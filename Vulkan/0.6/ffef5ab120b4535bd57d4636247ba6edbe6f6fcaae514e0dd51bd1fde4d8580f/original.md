Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `instance::Instance`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEnumeratePhysicalDeviceGroups.html)

```julia
_enumerate_physical_device_groups(
    instance
) -> ResultTypes.Result{Vector{Vulkan._PhysicalDeviceGroupProperties}, Vulkan.VulkanError}

```
