拡張: VK*EXT*opacity_micromap

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `create_info::MicromapCreateInfoEXT`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateMicromapEXT.html)

```julia
create_micromap_ext(
    device,
    create_info::Vulkan.MicromapCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.MicromapEXT, Vulkan.VulkanError}

```
