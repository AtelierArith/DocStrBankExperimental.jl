引数:

  * `device::Device`
  * `private_data_slot::PrivateDataSlot` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyPrivateDataSlot.html)

```julia
destroy_private_data_slot(
    device,
    private_data_slot;
    allocator
)

```
