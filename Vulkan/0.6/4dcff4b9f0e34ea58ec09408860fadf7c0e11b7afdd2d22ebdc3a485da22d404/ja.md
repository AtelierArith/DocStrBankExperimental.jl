拡張: VK*NV*dedicated_allocation

引数:

  * `dedicated_allocation::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDedicatedAllocationBufferCreateInfoNV.html)

```julia
_DedicatedAllocationBufferCreateInfoNV(
    dedicated_allocation::Bool;
    next
) -> Vulkan._DedicatedAllocationBufferCreateInfoNV

```
