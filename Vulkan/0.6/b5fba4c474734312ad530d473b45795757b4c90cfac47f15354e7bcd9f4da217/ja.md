拡張: VK*NVX*binary_import

引数:

  * `device::Device`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuModuleNVX.html)

```julia
CuModuleNVX(
    device,
    data_size::Integer,
    data::Ptr{Nothing};
    allocator,
    next
) -> Vulkan.CuModuleNVX

```
