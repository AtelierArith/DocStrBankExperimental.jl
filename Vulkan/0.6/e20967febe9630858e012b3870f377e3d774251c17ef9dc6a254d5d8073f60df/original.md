Arguments:

  * `initial_data::Ptr{Cvoid}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::PipelineCacheCreateFlag`: defaults to `0`
  * `initial_data_size::UInt`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCacheCreateInfo.html)

```julia
PipelineCacheCreateInfo(
    initial_data::Ptr{Nothing};
    next,
    flags,
    initial_data_size
) -> Vulkan.PipelineCacheCreateInfo

```
