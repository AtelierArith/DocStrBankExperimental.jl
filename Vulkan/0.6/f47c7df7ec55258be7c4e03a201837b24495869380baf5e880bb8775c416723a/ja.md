引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::FenceCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFenceCreateInfo.html)

```julia
_FenceCreateInfo(; next, flags) -> Vulkan._FenceCreateInfo

```
