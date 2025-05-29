拡張: VK*KHR*external*fence*fd

引数:

  * `fence::Fence`
  * `handle_type::ExternalFenceHandleTypeFlag`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFenceGetFdInfoKHR.html)

```julia
FenceGetFdInfoKHR(
    fence::Vulkan.Fence,
    handle_type::Vulkan.ExternalFenceHandleTypeFlag;
    next
) -> Vulkan.FenceGetFdInfoKHR

```
