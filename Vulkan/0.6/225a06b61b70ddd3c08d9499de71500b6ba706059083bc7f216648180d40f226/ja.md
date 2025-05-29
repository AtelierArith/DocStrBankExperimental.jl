拡張: VK*KHR*external*fence*fd

引数:

  * `fence::Fence` (externsync)
  * `handle_type::ExternalFenceHandleTypeFlag`
  * `fd::Int`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::FenceImportFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportFenceFdInfoKHR.html)

```julia
_ImportFenceFdInfoKHR(
    fence,
    handle_type::Vulkan.ExternalFenceHandleTypeFlag,
    fd::Integer;
    next,
    flags
) -> Vulkan._ImportFenceFdInfoKHR

```
