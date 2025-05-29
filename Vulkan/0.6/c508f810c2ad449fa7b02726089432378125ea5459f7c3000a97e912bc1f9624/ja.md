引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::EventCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkEventCreateInfo.html)

```julia
_EventCreateInfo(; next, flags) -> Vulkan._EventCreateInfo

```
