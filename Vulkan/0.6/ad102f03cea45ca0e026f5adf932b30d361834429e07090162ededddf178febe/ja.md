引数:

  * `initial_data::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::PipelineCacheCreateFlag`: デフォルトは `0`
  * `initial_data_size::UInt`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCacheCreateInfo.html)

```julia
_PipelineCacheCreateInfo(
    initial_data::Ptr{Nothing};
    next,
    flags,
    initial_data_size
) -> Vulkan._PipelineCacheCreateInfo

```
