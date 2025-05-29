拡張: VK*EXT*opacity_micromap

戻りコード:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `info::_CopyMicromapToMemoryInfoEXT`
  * `deferred_operation::DeferredOperationKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCopyMicromapToMemoryEXT.html)

```julia
_copy_micromap_to_memory_ext(
    device,
    info::Vulkan._CopyMicromapToMemoryInfoEXT;
    deferred_operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
