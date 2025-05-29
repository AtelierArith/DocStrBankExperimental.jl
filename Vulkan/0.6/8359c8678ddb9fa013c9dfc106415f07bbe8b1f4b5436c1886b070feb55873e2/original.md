Arguments:

  * `device_mask::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::MemoryAllocateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryAllocateFlagsInfo.html)

```julia
_MemoryAllocateFlagsInfo(
    device_mask::Integer;
    next,
    flags
) -> Vulkan._MemoryAllocateFlagsInfo

```
