引数:

  * `topology::PrimitiveTopology`
  * `primitive_restart_enable::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineInputAssemblyStateCreateInfo.html)

```julia
_PipelineInputAssemblyStateCreateInfo(
    topology::Vulkan.PrimitiveTopology,
    primitive_restart_enable::Bool;
    next,
    flags
) -> Vulkan._PipelineInputAssemblyStateCreateInfo

```
