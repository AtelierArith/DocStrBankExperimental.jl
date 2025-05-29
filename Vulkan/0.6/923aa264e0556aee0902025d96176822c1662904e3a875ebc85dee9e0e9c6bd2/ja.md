拡張: VK*NVX*binary_import

引数:

  * `device::Device`
  * `_module::CuModuleNVX`
  * `name::String`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuFunctionNVX.html)

```julia
CuFunctionNVX(
    device,
    _module,
    name::AbstractString;
    allocator,
    next
) -> Vulkan.CuFunctionNVX

```
