Arguments:

  * `initial_data::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PipelineCacheCreateFlag`: defaults to `0`
  * `initial_data_size::UInt`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCacheCreateInfo.html)

```julia
_PipelineCacheCreateInfo(
    initial_data::Ptr{Nothing};
    next,
    flags,
    initial_data_size
) -> Vulkan._PipelineCacheCreateInfo

```
