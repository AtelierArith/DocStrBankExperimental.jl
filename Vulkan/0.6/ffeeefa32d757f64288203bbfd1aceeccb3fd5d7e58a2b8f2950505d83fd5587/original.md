Extension: VK_KHR_external_fence_fd

Arguments:

  * `fence::Fence`
  * `handle_type::ExternalFenceHandleTypeFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFenceGetFdInfoKHR.html)

```julia
FenceGetFdInfoKHR(
    fence::Vulkan.Fence,
    handle_type::Vulkan.ExternalFenceHandleTypeFlag;
    next
) -> Vulkan.FenceGetFdInfoKHR

```
