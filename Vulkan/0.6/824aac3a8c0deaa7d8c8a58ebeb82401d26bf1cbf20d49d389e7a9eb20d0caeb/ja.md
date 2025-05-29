返すコード：

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数：

  * `device::Device`
  * `flags::UInt32`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePrivateDataSlot.html)

```julia
create_private_data_slot(
    device,
    flags::Integer;
    allocator,
    next
) -> ResultTypes.Result{Vulkan.PrivateDataSlot, Vulkan.VulkanError}

```
