引数:

  * `device::Device`
  * `flags::UInt32`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePrivateDataSlot.html)

```julia
PrivateDataSlot(
    device,
    flags::Integer;
    allocator,
    next
) -> Vulkan.PrivateDataSlot

```
