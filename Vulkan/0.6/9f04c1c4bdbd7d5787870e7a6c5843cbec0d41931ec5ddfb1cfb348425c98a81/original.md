Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_LAYER_NOT_PRESENT`
  * `ERROR_EXTENSION_NOT_PRESENT`
  * `ERROR_INCOMPATIBLE_DRIVER`

Arguments:

  * `create_info::_InstanceCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateInstance.html)

```julia
_create_instance(
    create_info::Vulkan._InstanceCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Instance, Vulkan.VulkanError}

```
