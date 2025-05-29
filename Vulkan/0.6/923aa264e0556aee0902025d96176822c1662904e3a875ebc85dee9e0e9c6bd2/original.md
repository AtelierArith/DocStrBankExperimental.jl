Extension: VK_NVX_binary_import

Arguments:

  * `device::Device`
  * `_module::CuModuleNVX`
  * `name::String`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuFunctionNVX.html)

```julia
CuFunctionNVX(
    device,
    _module,
    name::AbstractString;
    allocator,
    next
) -> Vulkan.CuFunctionNVX

```
