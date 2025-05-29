返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `bindings::Vector{DescriptorSetLayoutBinding}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorSetLayout.html)

```julia
create_descriptor_set_layout(
    device,
    bindings::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.DescriptorSetLayout, Vulkan.VulkanError}

```
