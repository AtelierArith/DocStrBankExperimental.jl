拡張: VK*KHR*external*fence*fd

引数:

  * `fence::Fence` (externsync)
  * `handle_type::ExternalFenceHandleTypeFlag`
  * `fd::Int`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::FenceImportFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportFenceFdInfoKHR.html)

```julia
ImportFenceFdInfoKHR(
    fence::Vulkan.Fence,
    handle_type::Vulkan.ExternalFenceHandleTypeFlag,
    fd::Integer;
    next,
    flags
) -> Vulkan.ImportFenceFdInfoKHR

```
