Extension: VK_KHR_external_fence_fd

Arguments:

  * `fence::Fence` (externsync)
  * `handle_type::ExternalFenceHandleTypeFlag`
  * `fd::Int`
  * `next::Any`: defaults to `C_NULL`
  * `flags::FenceImportFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportFenceFdInfoKHR.html)

```julia
ImportFenceFdInfoKHR(
    fence::Vulkan.Fence,
    handle_type::Vulkan.ExternalFenceHandleTypeFlag,
    fd::Integer;
    next,
    flags
) -> Vulkan.ImportFenceFdInfoKHR

```
