拡張: VK*NVX*binary_import

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuModuleNVX.html)

```julia
_create_cu_module_nvx(
    device,
    data_size::Integer,
    data::Ptr{Nothing};
    allocator,
    next
) -> ResultTypes.Result{Vulkan.CuModuleNVX, Vulkan.VulkanError}

```
