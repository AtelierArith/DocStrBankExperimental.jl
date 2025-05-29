返すコード：

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数：

  * `device::Device`
  * `create_info::PrivateDataSlotCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePrivateDataSlot.html)

```julia
create_private_data_slot(
    device,
    create_info::Vulkan.PrivateDataSlotCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.PrivateDataSlot, Vulkan.VulkanError}

```
