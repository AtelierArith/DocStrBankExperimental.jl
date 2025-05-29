引数:

  * `device_mask::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::MemoryAllocateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryAllocateFlagsInfo.html)

```julia
_MemoryAllocateFlagsInfo(
    device_mask::Integer;
    next,
    flags
) -> Vulkan._MemoryAllocateFlagsInfo

```
