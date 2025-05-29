Extension: VK_KHR_external_fence_fd

Arguments:

  * `fence::Fence`
  * `handle_type::ExternalFenceHandleTypeFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFenceGetFdInfoKHR.html)

```julia
_FenceGetFdInfoKHR(
    fence,
    handle_type::Vulkan.ExternalFenceHandleTypeFlag;
    next
) -> Vulkan._FenceGetFdInfoKHR

```
