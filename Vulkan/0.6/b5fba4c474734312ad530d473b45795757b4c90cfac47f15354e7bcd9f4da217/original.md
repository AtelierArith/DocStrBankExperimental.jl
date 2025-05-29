Extension: VK_NVX_binary_import

Arguments:

  * `device::Device`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuModuleNVX.html)

```julia
CuModuleNVX(
    device,
    data_size::Integer,
    data::Ptr{Nothing};
    allocator,
    next
) -> Vulkan.CuModuleNVX

```
