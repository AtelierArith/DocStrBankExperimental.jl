Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

Arguments:

  * `device::Device`
  * `create_info::SamplerCreateInfo`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSampler.html)

```julia
create_sampler(
    device,
    create_info::Vulkan.SamplerCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Sampler, Vulkan.VulkanError}

```
