返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_FRAGMENTED_POOL`
  * `ERROR_OUT_OF_POOL_MEMORY`

引数:

  * `device::Device`
  * `allocate_info::DescriptorSetAllocateInfo` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAllocateDescriptorSets.html)

```julia
allocate_descriptor_sets(
    device,
    allocate_info::Vulkan.DescriptorSetAllocateInfo
) -> ResultTypes.Result{Vector{Vulkan.DescriptorSet}, Vulkan.VulkanError}

```
