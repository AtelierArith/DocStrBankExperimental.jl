Arguments:

  * `topology::PrimitiveTopology`
  * `primitive_restart_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineInputAssemblyStateCreateInfo.html)

```julia
_PipelineInputAssemblyStateCreateInfo(
    topology::Vulkan.PrimitiveTopology,
    primitive_restart_enable::Bool;
    next,
    flags
) -> Vulkan._PipelineInputAssemblyStateCreateInfo

```
