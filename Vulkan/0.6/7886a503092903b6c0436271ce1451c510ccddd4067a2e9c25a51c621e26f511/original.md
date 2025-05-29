Extension: VK_EXT_opacity_micromap

Return codes:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `info::_CopyMicromapInfoEXT`
  * `deferred_operation::DeferredOperationKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCopyMicromapEXT.html)

```julia
_copy_micromap_ext(
    device,
    info::Vulkan._CopyMicromapInfoEXT;
    deferred_operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
