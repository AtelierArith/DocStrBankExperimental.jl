Extension: VK_KHR_external_memory_fd

Arguments:

  * `fd::Int`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `handle_type::ExternalMemoryHandleTypeFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportMemoryFdInfoKHR.html)

```julia
_ImportMemoryFdInfoKHR(fd::Integer; next, handle_type)

```
