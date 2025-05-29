拡張: VK*EXT*opacity_micromap

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `create_info::_MicromapCreateInfoEXT`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateMicromapEXT.html)

```julia
_create_micromap_ext(
    device,
    create_info::Vulkan._MicromapCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.MicromapEXT, Vulkan.VulkanError}

```
