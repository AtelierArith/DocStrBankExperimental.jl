引数:

  * `depth_test_enable::Bool`
  * `depth_write_enable::Bool`
  * `depth_compare_op::CompareOp`
  * `depth_bounds_test_enable::Bool`
  * `stencil_test_enable::Bool`
  * `front::StencilOpState`
  * `back::StencilOpState`
  * `min_depth_bounds::Float32`
  * `max_depth_bounds::Float32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::PipelineDepthStencilStateCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDepthStencilStateCreateInfo.html)

```julia
PipelineDepthStencilStateCreateInfo(
    depth_test_enable::Bool,
    depth_write_enable::Bool,
    depth_compare_op::Vulkan.CompareOp,
    depth_bounds_test_enable::Bool,
    stencil_test_enable::Bool,
    front::Vulkan.StencilOpState,
    back::Vulkan.StencilOpState,
    min_depth_bounds::Real,
    max_depth_bounds::Real;
    next,
    flags
) -> Vulkan.PipelineDepthStencilStateCreateInfo

```
