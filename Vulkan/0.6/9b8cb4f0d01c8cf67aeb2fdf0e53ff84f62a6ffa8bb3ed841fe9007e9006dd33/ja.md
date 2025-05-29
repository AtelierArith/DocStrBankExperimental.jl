引数:

  * `device_mask::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::MemoryAllocateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryAllocateFlagsInfo.html)

```julia
MemoryAllocateFlagsInfo(
    device_mask::Integer;
    next,
    flags
) -> Vulkan.MemoryAllocateFlagsInfo

```
