Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::SamplerYcbcrConversionCreateInfo`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSamplerYcbcrConversion.html)

```julia
create_sampler_ycbcr_conversion(
    device,
    create_info::Vulkan.SamplerYcbcrConversionCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.SamplerYcbcrConversion, Vulkan.VulkanError}

```
