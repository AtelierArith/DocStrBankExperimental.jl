拡張: VK*KHR*external*memory*fd

引数:

  * `fd::Int`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `handle_type::ExternalMemoryHandleTypeFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportMemoryFdInfoKHR.html)

```julia
_ImportMemoryFdInfoKHR(fd::Integer; next, handle_type)

```
