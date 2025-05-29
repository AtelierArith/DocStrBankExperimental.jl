戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `create_info::SamplerCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSampler.html)

```julia
create_sampler(
    device,
    create_info::Vulkan.SamplerCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Sampler, Vulkan.VulkanError}

```
