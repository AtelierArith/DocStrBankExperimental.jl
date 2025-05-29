戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `flags::UInt32`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePrivateDataSlot.html)

```julia
_create_private_data_slot(
    device,
    flags::Integer;
    allocator,
    next
) -> ResultTypes.Result{Vulkan.PrivateDataSlot, Vulkan.VulkanError}

```
